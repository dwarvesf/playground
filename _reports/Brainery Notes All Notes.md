
```dataviewjs
const query = dv.page("_queries").structured_permanent_notes_all;
const pagesQuery = await dv.query(query);
const { headers, values } = pagesQuery.value

dv.table(headers, values);
```
