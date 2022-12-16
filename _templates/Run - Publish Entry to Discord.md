<%*
const dv = this.app.plugins.plugins["dataview"].api;
const page = dv.page("_env");

const pageFields = Object.keys(page).filter(e => e.contains("discord_webhook"));
const field = await tp.system.suggester(items = pageFields, text_items = pageFields, throw_on_cancel=true, placeholder = "")
const webhookURL = page[field];

const contentNoFrontmatter = tp.file.content
	.replace(/---((.|\n)*)---/g, "")
const bareContent = contentNoFrontmatter
	.replace(/^(#+(.*))$/gm, "\n")
	.replace(/(\[\[|\]\])/gm, "")
	.replace(/(\r\n|\n|\r)/gm, "")
	.replace(/- (\w*)/gm, "");
const description = bareContent.split(" ").slice(0, 50).join(' ') + "..."

const currentPage = tp.file.folder();
const title = tp.file.title;
const braineryURL = "https://brain.d.foundation/" + encodeURIComponent(`${currentPage}/${title}`)
const author = `${tp.frontmatter.author}\n\n\*\*GitHub\*\*\n[${tp.frontmatter.github_id}](https://github.com/${tp.frontmatter.github_id})`;
const tags = tp.file.tags.slice(0, 5).join("\n") + " ..."
const footerText = `Added at ${tp.date.now("MMMM D, YYYY h:mm A")} 🎉🎉🎉` ;

const webhookBody = {
	username: "Brainery",
	avatar_url:  "https://cdn.discordapp.com/icons/462663954813157376/79ac3a24cf98b3c89be3902ca6fe168f.webp?size=96",
	embeds: [
		{
			title,
			url: braineryURL,
			description,
			fields: [
			  { name: "Author", value: author, inline: true },
			  { name: "Tags", value: tags, inline: true },
			],
			footer: {
				text: footerText
			}
		}
	]
}

const headers = {
	"Content-Type": "application/json",
}

await requestUrl({
	url: webhookURL,
	method: "POST",
	body: JSON.stringify(webhookBody),
	headers,
});
%>