控制器
===========
根据用户请求URL映射到控制器的动作来处理用户请求并相应。
控制器可以被看作是一个中介，只负责转发请求，调用模型对请求进行处理，通过视图响应。

1、控制器命名及文件约定
-----------------------
### 1.1、控制器文件命名约定
所有类（包括控制器）文件命名约定为：   
类文件都放在src文件夹子目录中，命名空间为子文件夹，文件名为类名后面加上".php"，一个类放一个文件，这样为了自动加载类以及方便找到类。
```
$file = str_replace('\\', '/', "src/{$namespace}/{$className}.php");
```

### 1.2、命名空间约定
控制器命名空间为
```
module\{$mod}\controller;
```
支持子命名空间
```
module\{$mod}\controller\子命名空间;
```
### 1.3、控制器类命名约定
类名以大写开头，使用驼峰法则，以Controller结尾。例如
```
AccountController
UploadController
MyDemoController
```
### 1.4、控制器类必须继承 \wf\mvc\Controller类

### 1.5、控制器方法名
我们把控制器方法名叫动作（action）。
控制器方法名后面带Action字符串。

管理操作方法名约定：管理后台控制器一般使用list、create、update、delete作为action名。
前台常用action名约定：indexAction、categoryAction、itemAction


### 1.6、其他
每个类需要有文档注释，以文件注释开头，在类声明前添加类文档注释。

### 1.7、控制器类完整案例
```
<?php
/**
 * Windwork
 * 
 * 一个高效的开源 PHP Web 开发框架
 * 
 * @copyright   Copyright (c) 2008-2015 Windwork Team. (http://www.windwork.org)
 * @license     http://opensource.org/licenses/MIT	MIT License
 */
namespace module\user\controller;

/**
 * 用户账号功能控制器
 * 
 * 用户登录、注册、忘记密码等功能实现
 * 
 * @package     module.user.controller
 * @author      erzh <cm@windwork.org>
 * @since       1.0
 */
class AccountController extends \wf\mvc\Controller {
    public function loginAction() {
        // to do sth.
    }
}
```


2、请求URL映射到控制器
-----------------------
详细文档见[Router](wf.mvc.router.html)
在查询字符串开头为url映射参数，映射参数为：模块.控制器.动作
例如：
```
index.php?$mod.$ctl.$act
index.php?user.account.login
```

控制器可以有子命名空间，用“.”隔开，如 
```
$namespace = str_replace(‘.’, ‘\\’, “\\module\\{$mod}\\{$ctl}”);

index.php?article.admin.category.list 
打开文件
src/module/article/controller/admin/CategoryController.php
执行
\module\article\controller\admin\CategoryController::listAction()

index.php?article.admin.biz.history.list 
打开文件
src/module/article/controller/admin/biz/HistoryController.php
执行
\module\article\controller\admin\biz\HistoryController::listAction()
```

3、在控制器动作中获取外部变量
-------------------------
我们把从客户端通过传递到服务器端的$_GET/$_POST/$_REQUEST/$_COOKIE变量称为外部变量。
我们使用\wf\Request类的实例获取外部变量。
```
class AccountController extends \wf\mvc\Controller {
    public function loginAction() {
        //读取$_GET变量
        $this->request->getGet('name'); // $_GET['name'] || null
        $this->request->getGet(); // $_GET

        //读取$_POST变量
        $this->request->getPost('name'); // $_POST['name'] || null
        $this->request->getPost(); // $_POST

        //读取$_REQUEST变量
        $this->request->getRequest('name'); // $_REQUEST['name'] || null
        $this->request->getRequest(); // $_REQUEST

        //读取$_COOKIE变量
        $this->request->getCookie('name'); // $_COOKIE['name'] || null
        $this->request->getCookie(); // $_COOKIE
    }
}
```

4、在控制器中使用模板视图
------------------
**模板变量赋值：** $this->view()->assign('变量', "值"); 变量名为字符串，值为任意数据类型。   
**显示模板：** $this->view()->render($tpl = '模板文件');  
模板文件夹按模块放在src/template/文件夹中，如果render()参数为空，则自动查询路径为src/template/default/{$mod}/{$ctl}.{$act}.html
```
class AccountController extends \wf\mvc\Controller {
    public function loginAction() {
        // 模板变量赋值
        $this->view()->assign('time', time());

        // 显示模板 src/template/default/user/account.login.html
        $this->view()->render();

        // 显示模板 src/template/default/user/account.login.m.html
        $this->view()->render('user/account.login.m.html');
    }
}
```

5、在控制器中使用模型
-----------------------
模型类放在模块文件夹下的model文件夹中，以Model为后缀，如：\module\user\model\UserModel
详细模型帮助文档见[模型](mvc_model.html)
```
class AccountController extends \wf\mvc\Controller {
    public function loginAction() {
        // 使用模型
        $userObj = new \module\user\model\UserModel();

        // 执行模型业务逻辑
        if(false !== $userObj->doLogin($params)) {
            Message::setOK('登录成功！');
        } else {
            Message::setErr($userObj->getErrs());
        }
        $this->showMessage();
    }
}
```
6、消息传递
--------------------
在程序执行流程中，消息从模型传递到控制器，然后再从控制器设置到消息管理器，视图显示的时候自动从消息管理器获取信息。详见[消息约定](message.html)
```
class AccountController extends \wf\mvc\Controller {
    public function loginAction() {
        $userObj = new \module\user\model\UserModel();

        // 执行模型业务逻辑
        if(false !== $userObj->doLogin($params)) {
            Message::setOK('登录成功！');
        } else {
            //业务逻辑有错误消息
            $errs = $userObj->getErrs();
            //把错误消息传递给消息管理器
            Message::setErr();
        }
        $this->showMessage();
    }
}
```
