This is a [[Map of Content]] related to the engineering concepts around data.

## General data
---
<%*
const dv = this.app.plugins.plugins["dataview"].api ;
const te = await dv.queryMarkdown(`LIST FROM #engineering/data AND -#big-data AND -#state`)
tR += te.value
%>
## Big data
---
<%*
const dv1 = this.app.plugins.plugins["dataview"].api ;
const te1 = await dv.queryMarkdown(`LIST FROM "" WHERE contains(tags, "big-data")`)
tR += te1.value
%>
## State
---
<%*
const dv2 = this.app.plugins.plugins["dataview"].api ;
const te2 = await dv.queryMarkdown(`LIST FROM "" WHERE contains(tags, "state")`)
tR += te2.value
%>
