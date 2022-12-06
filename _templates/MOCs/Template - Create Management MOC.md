---
recurringTemplate: true
recurringTemplateName: engineering-management-moc
---

This is a [[Map of Content]] related to the engineering concepts around management.

## Management
---
<%*
const dv = this.app.plugins.plugins["dataview"].api;
const te = await dv.queryMarkdown(`LIST FROM #engineering/management`);
tR += te.value;
%>
## Fundamentals
---
<%*
const te1 = await dv.queryMarkdown(`LIST FROM #fundamental`);
tR += te1.value;
%>

*This page was last modified at <%* tR += new Date().toISOString();%>*.
