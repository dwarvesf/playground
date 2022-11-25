## Notes submitted within past week

```dataview
TABLE
	"https://brain.d.foundation/%CE%A9+Fleeting+notes/" + rows.file.name as entries,
	rows.file.tags as tags,
	sum(rows.icy) + " ICY" as reward
FROM "Ω Fleeting notes"
WHERE discord_id != NULL
	AND date.weekyear >= (date(today)).weekyear
GROUP BY discord_id
```

### Literature & Permanent Notes

#### Literature Notes
```dataview
TABLE
	"https://brain.d.foundation/%CE%A9+Literature+notes/" + rows.file.name as entries,
	rows.file.tags as tags,
	sum(rows.icy) + " ICY" as reward
FROM "Ω Literature notes"
WHERE discord_id != NULL
	AND date.weekyear >= (date(today)).weekyear
GROUP BY discord_id
```

#### Permanent Notes
```dataview
TABLE
	"https://brain.d.foundation/%CE%A9+Permanent+notes/" + rows.file.name as entries,
	sum(rows.icy) + " ICY" as reward
FROM "Ω Permanent notes"
WHERE discord_id != NULL
	AND date.weekyear >= (date(today)).weekyear
GROUP BY discord_id
```

#### Structured Permanent Notes
```dataview
TABLE
	rows.file.link as entries, 
	rows.file.tags as tags
FROM #engineering OR #writing OR #design OR #communication OR #blockchain
WHERE author != NULL
	AND date.weekyear >= (date(today)).weekyear
GROUP BY author
```

