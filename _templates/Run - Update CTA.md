<%*
const dv = this.app.plugins.plugins["dataview"].api;
const pages = dv.pages(`"Blockchain" or "Communication" or "Design" or "Engineering" or "Writing"`);
const ctaTemplatePages = dv.pages(`"_templates/components/cta"`);
const ctaTemplate = ctaTemplatePages[0];

for (const element of pages) {
	// get folder and file path
	const file = app.vault.getAbstractFileByPath(element.file.path);
	const content = await app.vault.read(file);
	const ctaFile = app.vault.getAbstractFileByPath(ctaTemplate.file.path);
	const ctaContent = await app.vault.read(ctaFile);

	const ctaRegex = /<!-- cta -->/
	const hasCTA = ctaRegex.test(content);

	if (!hasCTA) {
		const joinedContent = content + ctaContent;
		await app.vault.modify(file, joinedContent);
	} else {
		const joinedContent = content.split("---\n<!-- cta -->")[0] + ctaContent;
		await app.vault.modify(file, joinedContent);
	}
}
%>