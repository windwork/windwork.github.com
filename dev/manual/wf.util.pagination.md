网页分页导航工具类
=======================

 通过设置总记录数、每页显示记录数来生成分页导航
 
## useage：

```
// 初始化
$totals = 1024; // 总条数
$rows = 10; // 每页显示条数

$pager = new \wf\util\Pagination($totals, $rows);

// 数据库查询分页参数
$offset = $pager->offset; // 当前页起始记录
$rows = $pager->rows; // 每页记录数

// 设置显示分页导航条
$this->view()->pager = $pager; // 视图变量约定为pager

// 视图中显示分页导航
{tpl base/pager}

```


## 详细案例

```
<?php

namespace module\article\controller;

class ShowController extends \wf\mvc\Controller {
    /**
     * 分页显示文章列表
     */
    public function listAction() {
        $cdt = array(
            'where' => array('status', 1),
            'order' => 'displayorder DESC, id DESC',
        );
        $articleObj = new \module\article\model\ArticleModel();
        
        // 符合条件的记录数
        $totals = $articleObj->count($cdt);
        
        // 分页类初始化，总记录数为$totals,每页显示10条记录
        $pager = new \wf\util\Pagination($totals, 10);
                
        // 数据库分页查询
        $list = $articleObj->find($cdt, $pager->offset, $pager->rows);

        $this->view()->assign('pager', $pager);
        $this->view()->assign('list', $list);
        
        $this->view()->render();
    }
}
```