模块配置
=======================
模块配置保存在模块文件夹中，文件名为 info.php

## 示例：
```
<?php
// src/module/demo/info.php
return [
    'name'         => '演示模块',       // 模块名称
	'description'  => '演示模块的简介', // 模块简介
	'homepage'     => 'http://windwork.org',  // 模块官网网址
	'license'      => 'MIT',
	
	// 作者，非必须
	'authors'      => [
						  [
						      'name' => 'CM',  // 作者姓名/昵称，必须
						      'email' => 'my@email.com', // 作者邮箱，非必须
						      'homepage' => 'http://windwork.org', // 作者主页，非必须
						  ]
					  ],
	'version'      => '1.0', // 模块版本
	'package'      => 'option', // 模块分组，core）核心模块；option）可选模块；other）其它模块，非官方开发者提供的模块选择该选项
	
	
	'require' => [
	    'wf' => '>=1.0', // wf开发框架版本要求
	],
];


```
## 选项说明
| 选项 | 类型 | 说明 |
|:----:|:----:|:-----|
|name        |string |模块名称|
|description |string |模块简介|
|homepage    |string |模块主页网址，如：http://windwork.org/|
|license     |string |模块使用协议，如：MIT、BSD、NewBSD、GPL等|
|version     |string |模块版本号|
|package     |string |模块分组，core）核心模块；option）可选模块；other）其它模块，非官方开发者提供的模块选择该选项|
|authors     |array  |模块作者信息，更详细的说明见后面|
|require     |array  |依赖模块，更详细的说明见后面|

### 作者信息
非必须，可以有一个或多个作者
```
'authors' => [
	[
	    'name' => '作者1',  // 作者姓名/昵称，必须
	    'email' => 'my@email.com', // 作者邮箱，非必须
	    'homepage' => 'http://windwork.org', // 作者主页，非必须
	],
	[
	    'name' => '作者2',
	    'email' => 'my@email.com',
	    'homepage' => 'http://windwork.org',
	],
]
```

### 依赖信息
模块依赖信息，非必须。
可设置模块所依赖的PHP版本，windwork框架版本、其他模块版本。

依赖版本值大小比较可以是>、>=、<、<=，
依赖版本范围值“版本A~版本B”表示依赖值为从版本A到版本B，比如：2.0~3.2表示>=2.0 并且 <= 3.2

```
'require' => [
    'wf'      => '>=1.0', // wf开发框架版本要求
	'php'     => '>=7.0',  // PHP版本要求，必须大于或等于windwork开发框架所需的PHP版本（5.5.0）
	'article' => '0.1~2.1', // 依赖article模块并只兼容从0.1.x到2.1.x的article模块。
],
```
