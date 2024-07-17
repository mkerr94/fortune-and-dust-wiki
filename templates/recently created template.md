
<%*
const dataViewApi = app.plugins.plugins["dataview"].api;
const fileName = "Recently Created";
const query = `TABLE file.ctime as "Creation Date" FROM "wiki" 
WHERE file.name != "Recently Updated" AND file.name != "Recently Created"
SORT file.ctime DESC LIMIT 8`;

const fileToOverwrite = tp.file.find_tfile(fileName);
const queryOutput = await dataViewApi.queryMarkdown(query);

await app.vault.modify(fileToOverwrite, queryOutput.value);
%>