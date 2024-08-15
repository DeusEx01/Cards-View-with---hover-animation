```dataviewjs
const table = dv.markdownTable(
  ["Cover"],
  dv
    .pages(`"05 - Library/01 - Books"`) //path where books are stored(folder in this case)
    .map((b) => {
      let cover;
      if (String(b.cover).includes("http")) { //`cover` - name of property with cover link
        cover = '<div class="img__wrap"><div class="img__img">' + "![coverimg](" + b.cover + ")" + "</div>"
      } else {
        cover = '<div class="img__wrap"><div class="img__img">' + "!" + b.cover + '</div>';
    }
    return [
          String(cover) + 
          '<div class="img__description_layer"><p class="img__description">' +
          '<span class="title">' + b.file.link + '</span>' +
          '<span class="property">· Author ·</span>'+ 
          `<span class="property_value">${b.author}</span>` + // `author` - name of property where author names is stored
          '<span class="property">· Rating ·</span>' +
          `<span class="property_value">${b.rate}</span>` + // `rate` - name of property where rating is stored
          '<span class="property">· Series ·</span>' +
          `<span class="property_value">${b.series}</span>` + // `series` - name of property where series name is stored
          '</div>'
      ]
    })
);
dv.el("div", table, { cls: "cardsMD" });
```
