## Fleeting Notes this month
```dataview
TABLE rows.file.link as entries
FROM "Ω Fleeting notes"
WHERE discord_id != NULL
	AND date.month = (date(today)).month
GROUP BY discord_id
```

## Fleeting Notes last month
```dataview
TABLE rows.file.link as entries
FROM "Ω Fleeting notes"
WHERE discord_id != NULL
	AND date.month = (date(today) - dur(1 month)).month
GROUP BY discord_id
```
