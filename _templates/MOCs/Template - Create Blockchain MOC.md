---
recurringTemplate: true
recurringTemplateName: blockchain-moc
---

This is a [[Map of Content]] related to the blockchain.

## Foundational Topics
---
<%*
const query = `LIST FROM #blockchain AND #foundational-topics`
const dv = this.app.plugins.plugins["dataview"].api ;
const te = await dv.queryMarkdown(query);
tR += te.value;
%>

## General
---
<%*
const query1 = `LIST FROM #blockchain AND !#foundational-topics`
const te1 = await dv.queryMarkdown(query1);
tR += te1.value;
%>

*This page was last modified at <%* tR += new Date().toISOString();%>*.