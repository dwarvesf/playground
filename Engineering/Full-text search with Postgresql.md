---
tags: engineering, database, SQL
author: Hoang Nguyen
---

## Note
Every example in this post will be demonstrated with Postgresql >= 11.x and using `tweets` table below with over 200k rows.

```sql
| tweets           |
|------------------|
| id(int)          |
| content(VARCHAR) |
| vector(tsvector) |
```

## What is Full-text search?

A **Full-text search (FTS)** Full Text Search refers to a technique in which you search for a single computer-stored document or a collection in your full-text database. It provides you with the capability to identify natural languages documents that satisfy a query..

## Why need Full-text search?
Normally when we want to search some words or text in a long sentence, we usually use `LIKE` operator

```sql
SELECT * FROM tweets WHERE content ILIKE '%something%'; 
```

It kinda simple, right! However, using `LIKE` operator with leading wildcard will make postgresql perform `Seq Scan` which mean database will skip using index for finding matched records. It will cause very low performance for big data table. Therefore, it it where `FTS` can be used to boost up the performance in query.

## Indexing

For normal columns, using [B-Tree index](https://dzone.com/articles/database-btree-indexing-in-sqlite) is the most common selection. However, in `FTS`, we should apply [GIN index](https://www.postgresql.org/docs/11/gin-intro.html) (**Generalized Inverted**). `GIN index` was designed to deal with data types that are subdividable and you want to search for individual component values (array elements, lexemes in a text document, etc). For simple explanation, `GIN index` like the table of contents in a book, where the heap pointers (to the actual table) are the page numbers. Multiple entries can be combined to yield a specific result.

## Stop words
For most human languages, there are some words which are not have any value in searching or analysing, those words is called stop-words. For example, In English some stop-words can be: `is, the, and, in, so,... etc`. Therefore, when we filter text, it should not count in out search string.

## Hands on
1. Create `GIN INDEX` for `vector` column:

```sql
CREATE INDEX idx_vector ON tweets USING GIN(vector);
```

1. Insert data to `vector` column

```sql
UPDATE
      tweets t
    SET
      vector = array_to_tsvector ((
          SELECT
            array_agg(DISTINCT substring(lexeme FOR len))
          FROM
            unnest(to_tsvector(LOWER(t."content"))),
            generate_series(1, length(lexeme)) len));
```

To explore what is exactly above query does? We can split it to simpler ones.

  - convert sentence to vector

  ```sql
  SELECT to_tsvector(LOWER('.@TataSky on which channel #WorldCupFinal #football is showing which ever is being tuned its paid channel.'));
  ```
  it will returns a vector where every token is a lexeme (a unit of lexical meaning) with its position in sentence.

  ```sql
  'channel':4,16 'ever':10 'footbal':6 'paid':15 'show':8 'tataski':1 'tune':13 'worldcupfin':5
  ```
  - converting vector into a table-like structure

  ```sql
  SELECT * FROM unnest(to_tsvector(LOWER('.@TataSky on which channel #WorldCupFinal #football is showing which ever is being tuned its paid channel.')));
  ```

  it will return a table-like structure for above vector.

| lexeme      | positions | weights |
|-------------|-----------|---------|
| channel     | {4,16}    | {D,D}   |
| ever        | {10}      | {D}     |
| footbal     | {6}       | {D}     |
| paid        | {15}      | {D}     |
| show        | {8}       | {D}     |
| tataski     | {1}       | {D}     |
| tune        | {13}      | {D}     |
| worldcupfin | {5}       | {D}     |

  - Get every substrings for each lexeme.

  ```sql
  SELECT
      DISTINCT substring(lexeme FOR len)
  FROM
    unnest(to_tsvector(LOWER('.@TataSky on which channel #WorldCupFinal #football is showing which ever is being tuned its paid channel.'))),
    generate_series(1, length(lexeme)) len;
  ```

  it will return every distinct substrings for every lexemes in the vector

  <details> 
    <summary>substrings </summary>

  ```sql
  ever
  tatask
  tun
  worldcupf
  wor
  ta
  worldcupfin
  tatas
  tu
  ch
  pa
  ev
  tat
  wo
  footbal
  worldcup
  foo
  worldcu
  channe
  chann
  c
  eve
  cha
  tata
  paid
  tune
  tataski
  e
  channel
  sho
  footb
  s
  w
  worldcupfi
  pai
  sh
  chan
  show
  worldc
  worl
  world
  f
  foot
  fo
  p
  t
  footba
  ```

  </details>


  ---> Therefore, at the end, every vector column record will have value like below:

  ```sql
  'c' 'ch' 'cha' 'chan' 'chann' 'channe' 'channel' 'e' 'ev' 'eve' 'ever' 'f' 'fo' 'foo' 'foot' 'footb' 'footba' 'footbal' 'p' 'pa' 'pai' 'paid' 's' 'sh' 'sho' 'show' 't' 'ta' 'tat' 'tata' 'tatas' 'tatask' 'tataski' 'tu' 'tun' 'tune' 'w' 'wo' 'wor' 'worl' 'world' 'worldc' 'worldcu' 'worldcup' 'worldcupf' 'worldcupfi' 'worldcupfin'
  ```

3. Query to find text.(it will use default English stop-words)

```sql
SELECT * FROM tweets WHERE vector @@ to_tsquery(REPLACE(LOWER('multiple words with no order'),' ', ' & '));
``` 

4. Custom Search configuration (OPTIONAL)

  - We can also configure the search configuration by our own like custom stop-words template
  
```sql
CREATE TEXT SEARCH DICTIONARY english_stem_nostop (
    Template = snowball
    , Language = english
);

CREATE TEXT SEARCH CONFIGURATION public.english_nostop ( COPY = pg_catalog.english );

ALTER TEXT SEARCH CONFIGURATION public.english_nostop
   ALTER MAPPING FOR asciiword, asciihword, hword_asciipart, hword, hword_part, word WITH english_stem_nostop;
```

- So in query to find text, it have some little change

```sql
SELECT * FROM tweets WHERE vector @@ to_tsquery('english_nostop',REPLACE(LOWER('multiple words with no order'),' ', ' & '));

```

## Result

It will be no sense if the result (performance) of this approach isn't better than normal way which using `LIKE` operator. So, let have some comparation.

<table>
<tr>
<th> LIKE operator </th>
<th> Full-text Search </th>
</tr>
<tr>
<td>

```sql
                                                                                                        
EXPLAIN ANALYZE SELECT * FROM tweets WHERE content ILIKE '%needles%well%' OR content ILIKE '%well%needles%';
```

| QUERY PLAN                                                                                                   |
|--------------------------------------------------------------------------------------------------------------|
| Seq Scan on tweets  (cost=0.00..134808.31 rows=40 width=1257) (actual time=775.639..1248.623 rows=4 loops=1) |
|   Filter: (((content)::text ~~* '%needles%well%'::text) OR ((content)::text ~~* '%well%needles%'::text))     |
|   Rows Removed by Filter: 206995                                                                             |
| Planning Time: 0.962 ms                                                                                      |
| Execution Time: 1248.754 ms                                                                                  |

</td>
<td>

```sql

EXPLAIN ANALYZE SELECT * FROM tweets WHERE vector @@ to_tsquery(REPLACE(LOWER('needles well'),' ', ' & '));
```
| QUERY PLAN                                                                                                                |
|---------------------------------------------------------------------------------------------------------------------------|
| Bitmap Heap Scan on tweets  (cost=44.42..137.34 rows=22 width=1257) (actual time=0.094..0.135 rows=4 loops=1)             |
|   Recheck Cond: (vector @@ to_tsquery('needles & well'::text))                                                            |
|   Heap Blocks: exact=4                                                                                                    |
|   ->  Bitmap Index Scan on idx_tweet_vector  (cost=0.00..44.41 rows=22 width=0) (actual time=0.074..0.081 rows=4 loops=1) |
|         Index Cond: (vector @@ to_tsquery('needles & well'::text))                                                        |
| Planning Time: 0.230 ms                                                                                                   |
| Execution Time: 0.231 ms                                                                                                  |

</td>
</tr>
</table>

--> The result show that the Planning time and execution time of `LIKE` operator is worse than `FTS` method. Because the demo is just illustrated on 200k records table. For larger table (millions records), the performance of using `LIKE` operator is much more worse than using `FTS` method. Besides that, you can notice that, with `FTS` we can search words with no orders required when in `LIKE` operator method, the words's order is also count to the result.

# References

- https://pganalyze.com/blog/gin-index
- https://wiki.postgresql.org/images/2/25/Full-text_search_in_PostgreSQL_in_milliseconds-extended-version.pdf
- https://www.compose.com/articles/mastering-postgresql-tools-full-text-search-and-phrase-search/
- SQL Performance Explained by Markus Winand (Book)
