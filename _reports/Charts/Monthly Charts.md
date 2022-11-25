## Tag Cloud

```chartsview
#-----------------#
#- chart type    -#
#-----------------#
type: WordCloud

#-----------------#
#- chart data    -#
#-----------------#
data: |
  dataviewjs:
    return dv.pages("#engineering OR #writing OR #design OR #communication OR #blockchain")
           .where(p => !!p.file.frontmatter.date)
           .where(p => dv.date(p.file.frontmatter.date) !== null)
           .where(p => dv.date(p.file.frontmatter.date).weekNumber >= dv.date('today').weekNumber - 4)
           .flatMap(p => p.file.etags)
           .filter(p => !(p.search(/#engineering|#writing|#design|#communication|#blockchain/g) > -1))
           .groupBy(p => p)
           .map(p => ({tag: p.key, count: p.rows.length}))
           .array();

#-----------------#
#- chart options -#
#-----------------#
options:
  wordField: "tag"
  weightField: "count"
  colorField: "count"
  enableSearchInteraction:
    operator: tag
```

## Tag Treemap

```chartsview
#-----------------#
#- chart type    -#
#-----------------#
type: Treemap

#-----------------#
#- chart data    -#
#-----------------#
data: |
  dataviewjs:
    const children = []
    const query = dv.pages("#engineering OR #writing OR #design OR #communication OR #blockchain")
        .where(p => !!p.file.frontmatter.date)
        .where(p => dv.date(p.file.frontmatter.date) !== null)
        .where(p => dv.date(p.file.frontmatter.date).weekNumber >= dv.date('today').weekNumber - 4)
        .flatMap(p => p.file.etags)
        .filter(p => !(p.search(/#engineering|#writing|#design|#communication|#blockchain/g) > -1)).values
        .reduce((a, p) => {
            if (!(p in a)) {
                a[p] = 0;
            } else {
                a[p] += 10;
            }
            return a;
        }, {})
    Object.entries(query).forEach(([key, value]) => {
        children.push({
            name: key,
            value,
        })
    })
    return {
        name: 'root',
        children,
    }

#-----------------#
#- chart options -#
#-----------------#
options:
  colorField: "name"
```

## Weighted Topic Radar

```chartsview
#-----------------#
#- chart type    -#
#-----------------#
type: Radar

#-----------------#
#- chart data    -#
#-----------------#
data: |
  dataviewjs:
    return dv.pages("#engineering OR #writing OR #design OR #communication OR #blockchain")
           .where(p => !!p.file.frontmatter.date)
           .where(p => dv.date(p.file.frontmatter.date) !== null)
           .where(p => dv.date(p.file.frontmatter.date).weekNumber >= dv.date('today').weekNumber - 4)
           .flatMap(p => p.file.etags)
           .filter(p => p.search(/#engineering|#writing|#design|#communication|#blockchain/g) > -1)
           .map(p => p.replace(/#(\w*)(.*)/, "$1")).values
           .reduce((a, p) => {
               switch (p) {
                   case "engineering": a[0].score += 1; break;
                   case "writing": a[1].score += 10; break;
                   case "design": a[2].score += 10; break;
                   case "communication": a[3].score += 10; break;
                   case "blockchain": a[4].score += 1; break;
               }
               return a;
           }, [
               {
                   item: "Engineering",
                   user: "a",
                   score: 0
               },
               {
                   item: "Writing",
                   user: "a",
                   score: 0
               },
               {
                   item: "Design",
                   user: "a",
                   score: 0
               },
               {
                   item: "Communication",
                   user: "a",
                   score: 0
               },
               {
                   item: "Blockchain",
                   user: "a",
                   score: 0
               },
           ])

#-----------------#
#- chart options -#
#-----------------#
options:
  xField: "item"
  yField: "score"
  seriesField: "user"
  meta:
    score:
      alias: "Score"
      min: 0
      nice: true
  xAxis:
    line: null
    tickLine: null
  yAxis:
    label: false
    grid:
      alternateColor: "rgba(0, 0, 0, 0.04)"
  point: {}
  area: {}
```

## Weighted Topic Treemap

```chartsview
#-----------------#
#- chart type    -#
#-----------------#
type: Treemap

#-----------------#
#- chart data    -#
#-----------------#
data: |
  dataviewjs:
    const children = dv.pages("#engineering OR #writing OR #design OR #communication OR #blockchain")
           .where(p => !!p.file.frontmatter.date)
           .where(p => dv.date(p.file.frontmatter.date) !== null)
           .where(p => dv.date(p.file.frontmatter.date).weekNumber >= dv.date('today').weekNumber - 4)
           .flatMap(p => p.file.etags)
           .filter(p => p.search(/#engineering|#writing|#design|#communication|#blockchain/g) > -1)
           .map(p => p.replace(/#(\w*)(.*)/, "$1")).values
           .reduce((a, p) => {
               switch (p) {
                   case "engineering": a[0].value += 1; break;
                   case "writing": a[1].value += 10; break;
                   case "design": a[2].value += 10; break;
                   case "communication": a[3].value += 10; break;
                   case "blockchain": a[4].value += 1; break;
               }
               return a;
           }, [
               {
                   name: "Engineering",
                   value: 0
               },
               {
                   name: "Writing",
                   value: 0
               },
               {
                   name: "Design",
                   value: 0
               },
               {
                   name: "Communication",
                   value: 0
               },
               {
                   name: "Blockchain",
                   value: 0
               },
           ])
    return {
        name: 'root',
        children,
    }

#-----------------#
#- chart options -#
#-----------------#
options:
  colorField: "name"
```

