<%*
const dataViewApi = app.plugins.plugins["dataview"].api;
const fileName = "Recently Updated";

const query = `TABLE file.mtime as "Last Modified"
FROM "wiki"
WHERE file.name != "Recently Updated" AND file.name != "Recently Created"
SORT file.mtime DESC
LIMIT 7`;

const fileToOverwrite = tp.file.find_tfile(fileName);
const queryOutput = await dataViewApi.queryMarkdown(query);

await app.vault.modify(fileToOverwrite, queryOutput.value);
%>