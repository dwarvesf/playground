## Engineering
```dataview
TABLE author, date, "#" + regexreplace(tags, ", ", " #") as tags
FROM #engineering
WHERE author != NULL
```

## Writing
```dataview
TABLE author, date, "#" + regexreplace(tags, ", ", " #") as tags
FROM #writing
WHERE author != NULL
```

## Design
```dataview
TABLE author, date, "#" + regexreplace(tags, ", ", " #") as tags
FROM #design
WHERE author != NULL
```

## Communication
```dataview
TABLE author, date, "#" + regexreplace(tags, ", ", " #") as tags
FROM #communication 
WHERE author != NULL
```

## Blockchain
```dataview
TABLE author, date, "#" + regexreplace(tags, ", ", " #") as tags
FROM #blockchain 
WHERE author != NULL
```
