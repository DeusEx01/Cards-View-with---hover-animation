```dataviewjs 
const table = dv.markdownTable(
  ["Cover"],
  dv
    .pages(`"05 - Library/01 - Books"`)
    .filter((b) => b.status == "done")
    .sort((b) => b.series)
    .map((b) => {
      if (b.cover.includes("http")) {
        return [
          '<div class="img__wrap"><div class="img__img">' +
            "![coverimg](" +
            b.cover +
            ")" +
            "</div>" +
            '<div class="img__description_layer"><p class="img__description">' +
            '<span class="title">' +
            b.file.link +
            "</span>" +
            '<span class="property">· Author ·</span>' +
            `<span class="property_value">${b.author}</span>` +
            "</div>",
        ];
      } else {
        return [
          '<div class="img__wrap"><div class="img__img">' + "!" + b.cover + '</div>' +
          '<div class="img__description_layer"><p class="img__description">' +
          '<span class="title">' + b.file.link + '</span>' +
          '<span class="property">· Author ·</span>'+ 
          `<span class="property_value">${b.author}</span>` +
          '<span class="property">· Rating ·</span>' +
          `<span class="property_value">${b.rate}</span>` +
          '<span class="property">· Series ·</span>' +
          `<span class="property_value">${b.series}</span>` +
          '</div>'
      ]
      }
    })
);
dv.el("div", table, { cls: "cardsMD" });
```
