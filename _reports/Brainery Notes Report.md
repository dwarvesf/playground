## Brainery submissions this month
```dataview
TABLE author, date, "#" + regexreplace(tags, ", ", " #") as tags
FROM #engineering OR #writing OR #design OR #communication OR #blockchain
WHERE author != NULL
	AND date.month = (date(today)).month
```

## Brainery submissions last month
```dataview
TABLE author, date, "#" + regexreplace(tags, ", ", " #") as tags
FROM #engineering OR #writing OR #design OR #communication OR #blockchain
WHERE author != NULL
	AND date.month = (date(today) - dur(1 month)).month
```
