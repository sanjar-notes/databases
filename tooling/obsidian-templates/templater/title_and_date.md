<%*
retVal = tp.file.title;
if (retVal.endsWith(".md")) retVal = retVal.slice(0, -3);

delimiter_sign = [...retVal].find(letter => letter === '_' || letter === '-');

completeTitle = retVal.replaceAll(delimiter_sign, " ");
potentialNumber = completeTitle.split(" ").at(0);
hasNumber = !Number.isNaN(parseFloat(potentialNumber));
titleWithoutNumber = completeTitle.slice(potentialNumber.length + 1);

newTitle = hasNumber
  ? `${potentialNumber}. ${titleWithoutNumber}`
  : completeTitle;
%># <% newTitle %>
<% tp.date.now("[Created] ddd ll [at] LT") %>

<% tp.file.cursor() %>