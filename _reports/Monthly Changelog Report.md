
## Notes submitted within past month
```dataviewjs
const query = dv.page("_queries").fleeting_monthly;
const pagesQuery = await dv.query(query);
const { headers, values } = pagesQuery.value

dv.table(headers, values);
```

### Literature & Permanent Notes
#### Structured Permanent Notes
```dataviewjs
const query = dv.page("_queries").structured_permanent_notes_monthly;
const pagesQuery = await dv.query(query);
const { headers, values } = pagesQuery.value

dv.table(headers, values);
```

#### Literature Notes
```dataviewjs
const query = dv.page("_queries").literature_notes_monthly;
const pagesQuery = await dv.query(query);
const { headers, values } = pagesQuery.value

dv.table(headers, values);
```

#### Permanent Notes
```dataviewjs
const query = dv.page("_queries").permanent_notes_monthly;
const pagesQuery = await dv.query(query);
const { headers, values } = pagesQuery.value

dv.table(headers, values);
```
