---
title: 关于微信分享的小坑
date: 2017-07-13
tags: ['WeChat share']
---
#### WeChat share 有关显示
在调用分享接口时，安卓部分手机可能显示有误，尝试在调用前延迟1500ms
<!-- more -->

#### 分享链接有关

在将链接分享时 微信会自动将location.search变为分享来源代码

 - 原始链接为

```js
http://localhost:3000/corp/#/full/try-vote-list?user=15652813691&user_id=710
```

- 经过微信分享给朋友后

```js
http://localhost:3000/corp/?from=singlemessage&isappinstalled=0#/full/try-vote-list?user=18896817619&user_id=777
```

- 在该页面下只改变参数进行跳转时，无效

```js
location.replace(`${location.origin}/corp/#/full/try-vote-list?user=${$scope.third}&user_id=${$scope.currentUser}`)

```
- 解决方式

```js
location.replace(`${location.origin}/corp/${location.search}#/full/try-vote-list?user=${$scope.third}&user_id=${$scope.currentUser}`)
```
在进入该页面时，匹配到 &isappinstalled=0，将其直接跳转至去除来源信息的链接