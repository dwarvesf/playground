## Fleeting Notes this month
```dataview
TABLE discord_id, discord_channel, date, "#" + regexreplace(tags, ", ", " #") as tags
FROM "Ω Fleeting notes"
WHERE discord_id != NULL
	AND date.month = (date(today)).month
```

## Fleeting Notes last month
```dataview
TABLE discord_id, discord_channel, date, "#" + regexreplace(tags, ", ", " #") as tags
FROM "Ω Fleeting notes"
WHERE discord_id != NULL
	AND date.month = (date(today) - dur(1 month)).month
```
