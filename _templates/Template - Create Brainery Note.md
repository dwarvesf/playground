---
tags:
author:
github_id:
date: <% await tp.file.creation_date("YYYY-MM-DD") %>
icy: 10
---

<%*
const dv = this.app.plugins.plugins["dataview"].api;
const pages = dv.pages(`"_templates/Template - CTA"`);

const element = pages[0]
const ctaFile = app.vault.getAbstractFileByPath(element.file.path);

const ctaContent = await app.vault.read(ctaFile);
tR += ctaContent;
%>