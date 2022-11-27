<%*
const dv = this.app.plugins.plugins["dataview"].api;
const recurringTemplatesList = dv.pages(`"_templates"`)
	.where(e => e.file.frontmatter.recurringTemplate);
const mappedRecurringTemplateNames = recurringTemplatesList.array().reduce((a, c) => {
	a[c.recurringTemplateName] = c.file.name
	return a;
}, {})

const matchingNotes = dv.pages(`!"_templates"`)
	.where(e => e.file.frontmatter.recurringTemplate);

for (const element of matchingNotes) {
	const { recurringTemplateName } = element
	const filePath = app.vault.getAbstractFileByPath(element.file.path);
	const folder = app.vault.getAbstractFileByPath(element.file.folder)

	// find the template
	const templatePath = mappedRecurringTemplateNames[recurringTemplateName];
	const template = tp.file.find_tfile(templatePath);

	// delete the file
	await app.vault.trash(filePath, true);

	console.log({ element, filePath, templatePath, template });
	// create a new file with the matching template
	await tp.file.create_new(template, element.file.name, false, folder);
}
%>