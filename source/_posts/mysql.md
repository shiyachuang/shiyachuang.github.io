---
title: MySql 语句整理
date: 2017-06-22 10:20:05
tags: MySql
---


> 查询结果第一种情况

**从第一个表里面拿出来的数据，作为表 a，第二个表作为 b， 第三个作为 c ，a 表中不满足  b 条件被删除，然后和 c 比对 ，不满足 c 被删除，剩下的数据再根据 a 的 where  查出结果**

join 代表链接

```js
rest.query('select * from 表名 ' a
join('select ··· from 表名 where 条件 ') b on a.id = b.id
join('select ··· from 表名 ') c on c.id = a.id where ' a.条件 and a.条件 '
)
```
<!-- more -->

> 查询结果第二种情况

**select时可以 a.属性名 b.属性名 as  name**

```js
rest.query('select a.id, b.id as auit_id, a.name, b.name as nikename...  from 表名 ' a
join('select ··· from 表名 where 条件 ') b on a.id = b.id where ' a.条件 and a.条件 '
)
```



3. > 查询数量

DISIINCT = 不重复
as = 作为count

```js
rest.queryOne(' count(DISTINCT(a.user_id)) as count from 表名 ' a join('select ··· from 表名 where 条件 ') b on a.id = b.id
join('select ··· from 表名 ') c on c.id = a.id where ' a.条件 and a.条件 '
)
```


```js
//点击图片，调用微信预览图片接口
    $scope.wxPreview = u => {
      wx.previewImage({
        current: location.origin + u.screen_shot,
        urls: [location.origin + u.screen_shot] // 需要预览的图片http链接列表
      });
    }

```