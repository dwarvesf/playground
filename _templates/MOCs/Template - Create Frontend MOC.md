---
recurringTemplate: true
recurringTemplateName: engineering-frontend-moc
---

This is a [[Map of Content]] related to the engineering concepts around frontend.

## General frontend
---
<%*
const dv = this.app.plugins.plugins["dataview"].api ;
const te = await dv.queryMarkdown(`LIST FROM #engineering/frontend AND -#a11y AND -#fundamental`);
tR += te.value;
%>
## Fundamentals
---
<%*
const te1 = await dv.queryMarkdown(`LIST FROM "" WHERE contains(tags, "fundamental")`);
tR += te1.value;
%>
## Accessibility
---
<%*
const te2 = await dv.queryMarkdown(`LIST FROM "" WHERE contains(tags, "a11y")`)
tR += te2.value;
%>

*This page was last modified at <%* tR += new Date().toISOString();%>*.
