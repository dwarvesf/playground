## Brainery submissions this month

```dataview
TABLE rows.file.link as entries
FROM #engineering OR #writing OR #design OR #communication OR #blockchain
WHERE author != NULL
	AND date.month = (date(today)).month
GROUP BY author
```


## Brainery submissions last month
```dataview
TABLE rows.file.link as entries
FROM #engineering OR #writing OR #design OR #communication OR #blockchain
WHERE author != NULL
	AND date.month = (date(today) - dur(1 month)).month
GROUP BY author
```
