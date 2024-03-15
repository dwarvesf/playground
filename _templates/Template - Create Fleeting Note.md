---
discord_id: <% await tp.system.prompt("Discord ID") %>
discord_channel: <% await tp.system.prompt("Discord Channel") %>
date: <% await tp.file.creation_date("YYYY-MM-DD") %>
tags: <% await tp.system.prompt("Tags") %>
icy: <% await tp.system.prompt("Rewarded ICY", "5") %>
---
<% await tp.file.rename(`${tp.file.creation_date("YYYYMMDDHHSS")}`) %>
<% await tp.system.prompt("Content", tp.system.clipboard(), false, true) %>