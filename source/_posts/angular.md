---
title: angular学习
date: 2017-07-12 00:23:06
tags: angular
---

## angular.js 学习
> 定义class的三种方法
<!-- more -->

```html
<html ng-app='myApp'>
<head>
<style>
.red{color: red;}.red2{color: #f0f;}
.red3{color: #00f;}.red4{color: #2ff;}
</style>
</head>
<body ng-controller="myCtrl">
	<p  ng-class="{{red}}">111</p>
	<p  ng-class="{true: 'red', false: 'red2'}[isActive]">222</p>
	<p  ng-class="{'red3': isSelected, 'red4': isCar}">444</p>
<script src="node_modules\angular\angular.min.js"></script>
<script>
	var app = angular.module('myApp', []);
	app.controller('myCtrl', function($scope) {
		$scope.red="red";
	   	$scope.isActive = false;
	    $scope.isSelected = true;
	    $scope.isCar = false;
	});
</script>
</body>
</html>
```