目录机构
===============

目录相关常量
-------------------
 * SRC_PATH 源码所在目录的完整路径
 * WEB_ROOT 网站入口目录的完整路径（在index.php里设置，  define('WEB_ROOT', str_replace('\\', '/', __DIR__) . '/');）
 
 
框架目录结构
-------------------
```
--+
  |- docs     文档目录
  |    |- dev  开发文档
  |    |- help 用户使用帮助文档
  |- install  安装脚本目录
  |- src      系统源码目录
  |    |- config   配置文件目录
  |    |- wf     系统核心框架
  |    |- data     站点动态数据保存目录
  |    |- language 语言包
  |    |- libs     第三方库
  |    |- module   模块文件夹
  |    |- template 模板目录
  |    |- test     单元测试目录
  |    |- compat.php 通用函数
  |- static   静态文件目录
  |- storage  附件存贮目录
  |- theme    模板主题样式
  |- index.php 系统入口
```

模块目录结构
-----------------------
```
src/module
      |- module1Name
      |- module1Name
      |- module3Name
```
