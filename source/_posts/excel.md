---
title: Excel 导出
date: 2017-07-04 23:44:46
tags: excel
---
> 先引入Excel 模板

```js
const xl = require('excel4node');//引入Excel模板
```
<!-- more -->

> 实例化工作簿

```js
let wb = new xl.Workbook()//实例化工作薄
ler ws = wb.addWorksheet('Sheet 1'), //实例化表
```

> 自定义style

```js
 const styleFont = {
    font: {
      color: '#000000',
      name: '宋体',
      size: 12
    },
    alignment: {
      horizontal: 'center'
    },
    numberFormat: '#,##0'
  };
//调用方法
ws.cell(1,2).string(value).style(styleFont);
```

> 设置每列的宽度

```js
//第一行从1-7列设置宽度40
_.range(1, 8).forEach((v, i) => {
    ws.column(++i).setWidth(40);
  })
```

> thead 设置

```js
const head_title = ['ID', '名字', '电话', '公司', '新增会员数', '新增健康记录', '新增消费记录']
  head_title.forEach((v, i) => {
    ws.cell(1, ++i).string(v).style(style.title);
  });
```

> 第一行合并

```js
// 第一行合并
// ws.cell(startRow, startColumn, [[endRow, endColumn], isMerged]);
//isMerged = '是否合并'
ws.cell(1, 1, 1, 15, true).string(titleRow).style(styleTitle);
```

> last 最后一步

```js
res.setHeader('Content-Type', 'application/vnd.openxmlformats-officedocument.spreadsheetml.sheet');

res.setHeader("Content-Disposition", `attachment; filename=${encodeURIComponent('会员信息数据')}.xlsx`);

wb.writeToBuffer().then(data => res.send(data));
```

---
**参考资料**
[https://www.npmjs.com/package/excel4node](https://www.npmjs.com/package/excel4node)