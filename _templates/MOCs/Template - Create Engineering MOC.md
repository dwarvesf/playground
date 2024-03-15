---
recurringTemplate: true
recurringTemplateName: engineering-moc
---

This is a [[Map of Content]] related to the engineering.

## Engineering

<%*
const query = `LIST FROM #engineering AND -#engineering/data AND -#engineering/backend AND -#engineering/frontend AND -#engineering/management AND -#engineering/mobile`
const dv = this.app.plugins.plugins["dataview"].api;
const te = await dv.queryMarkdown(query);
tR += te.value;
%>

*This page was last modified at <%* tR += new Date().toISOString();%>*.
