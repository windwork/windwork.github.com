开发文档编写规范
=================
本文档约定开发文档的编写规范，目的是使文档编写规范化，方便文档编写效率、可读性、传播等。

### 1、文档格式

我们的开发帮助文档使用 Markdown 语法，使用markdownpad编辑器进行编写。 
 
> [Markdown创始人的说明文档](http://daringfireball.net/projects/markdown/syntax)  
> [Markdown快速入门 1](http://www.ituring.com.cn/article/23)  
> [Markdown快速入门 2](http://wowubuntu.com/markdown/basic.html)  
> [Markdown编辑器下载](http://www.markdownpad.com/download.html)

文档可编辑文件放在docs/dev/manual文件夹，后缀为.md，文档编写好以后，用工具生成html版保存到 docs/manual文件夹，整个docs文件夹一起发布到官网，通过 http://www.windwork.org/manual/ 访问开发文档（通过URLRewrite重写到 http://www.windwork.org/docs/manual/）

### 2、文件名

文档文件命名规范：
 * 文件名全部小写
 * 根据框架类名及命名空间来命名，完整命名空间的类名把命名空间符"\"换成"."，加上“.md”后缀为可编辑帮助文档文件名，如：模型基类的帮助文档保存为“docs/dev/manual/wf.mvc.model.md”。
 * 没有对应类的重要帮助文档以“general.”开头。
 * 组件工厂的帮助文档文件名统一为将类的“命名空间”的"\"换成"."，加上“.md”后缀即可，不需要带类名。

### 3、图片
有时候帮助文档中需要插入图片，图片以英文命名，保存在docs/dev/manual/res/images文件夹。

