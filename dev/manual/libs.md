使用的第三方扩展
==================

PHP
------------
- PclZip 
  zip压缩解压
  http://www.phpconcept.net/pclzip/pclzip-downloads

- Snoopy
  HTTP客户端
  http://snoopy.sourceforge.net/

- phpmailer 
  https://github.com/PHPMailer/PHPMailer

- 

前端框架
--------------
- Bootstrap 
  github https://github.com/twbs/bootstrap
  官方网站 http://getbootstrap.com/
  中文文档 3.x http://v3.bootcss.com/

javascript
---------------

- js模块化 seajs http://seajs.org/ 
- 基础框架 
  jQuery http://www.jquery.com

- js插件
  - ~~消息窗口 noty https://github.com/needim/noty~~
  - 表单验证 jQuery.validation http://jqueryvalidation.org/ https://github.com/jzaefferer/jquery-validation
  - 日期选取 
    bootstrap-datepicker https://github.com/eternicode/bootstrap-datepicker
    bootstrap-datetimepicker
  - 颜色选取 bootstrap-colorpicker https://github.com/mjolnic/bootstrap-colorpicker/
  - 图片上传 FineUploader https://github.com/FineUploader/fine-uploader
  - 图片缩放预览 
    jquery.zoom https://github.com/jackmoore/zoom （jQuery 1.7+ in Chrome, Firefox, Safari, Opera, Internet Explorer 7+.）
    zoom.js https://github.com/fat/zoom.js

  - 图片剪切 Jcrop https://github.com/tapmodo/Jcrop
  - 图表 FusionCharts Free http://www.fusioncharts.com/free/
  - 延迟加载图片 jquery.lazyload https://github.com/tuupola/jquery_lazyload
  - 页面加载进度条 NProgress https://github.com/rstacruz/nprogress/

CDN
--------
- jQuery 
  http://cdn.bootcss.com/jquery/1.11.3/jquery.min.js
  http://cdn.bootcss.com/jquery/2.1.4/jquery.min.js
  更多在http://www.bootcdn.cn/jquery/

- Bootstrap 
  详见 http://www.bootcdn.cn/bootstrap/

- animate.css
  http://www.bootcdn.cn/animate.css/

很多开源前端框架cdn：http://www.bootcdn.cn/

其他工具
------------
- js/css压缩 yuicompressor.jar http://yui.github.io/yuicompressor/
  在命令行下压缩js/css文件
- PHP压缩js JShrink https://github.com/tedious/JShrink
- PHP压缩css $css = preg_replace(array('/[\t\n\r]/', '/\/\*.+?\*\//'), array('',''), $css);