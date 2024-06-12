#### 52 插件 Charts View 制作标签云（词云）

插件：Charts view
插件本身提供了很多模板，直接套用即可
需要更改的只是中间部分的数据
示例代码1

```
data:
	dataviewjs:
	return (() => {
		const tags = this.app.metadataCache.getTags();
		console.dir(tags);
		let dataArray = [];
		Object.keys(tags).forEach(key => dataArray.push({
			tag:key.replace("#",""),
			count: tags[key]
			}));
		return dataArray.filter(p => !p.tag.includes("<") && !p.tags.includes(">"));
	
	
	})();
	
```

示例代码2

```
data:
	dataviewjs:
	return dv.pages()
			.groupBy(p => p.file.folder)
			.sort(p => p.rows.length)
			.map(p => ({folder: p.key || "ROOT", count: p.rows.length}))
			.array()
			.reverse();
```