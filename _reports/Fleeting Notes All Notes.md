## Fleeting Notes
```dataview
TABLE discord_id, discord_channel, date, "#" + regexreplace(tags, ", ", " #") as tags, icy
FROM "Ω Fleeting notes"
WHERE discord_id != NULL
```
