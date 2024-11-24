<%*
const dataViewApi = app.plugins.plugins["dataview"].api;
const fileName = "Session List";

const query = `LIST FROM "wiki/The Adventure So Far" SORT file.ctime ASC`;

const fileToOverwrite = tp.file.find_tfile(fileName);
const queryOutput = await dataViewApi.queryMarkdown(query);

await app.vault.modify(fileToOverwrite, queryOutput.value);
%>