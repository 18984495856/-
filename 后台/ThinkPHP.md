# 数据创建和迁移

[教程文档](https://www.kancloud.cn/thinkphp/master-database-and-model/265553#_87)

### 简介

>  所谓迁移就像是数据库的版本控制，这种机制允许团队简单轻松的编辑并共享应用的数据库表结构。迁移通常和 Laravel 的 schema  构建器结对从而可以很容易地构建应用的数据库表结构。如果你曾经频繁告知团队成员需要手动添加列到本地数据库表结构以维护本地开发环境，那么这正是数据库迁移所致力于解决的问题。

相当于把你的数据库的增、删、查、改用文件的形式记录了下来，只要把这些文件交给别人，然后使用命令行运行这些文件，就能够得到一个和你一模一样的数据库。

### 作用

- 能够通过命令行生成迁移文件（PHP源代码），在迁移文件里面编写要创建或者修改以及删除表、列等的代码
- 使用命令行运行这些迁移文件，让php自动给我们创建数据库，实现自动创建表，添加缺失的列，修改原来的列名等等操作。

### 如何添加新列

```php
$this->table('user')
            ->addColumn(Column::string('header')->setComment('头像'))->save(); //主要要save
```

### 常用命令行

```
创建一个迁移文件：
php think migrate:create AddHeader //AddHeader是迁移文件名，必须是驼峰命名法，且大写字母开头。
运行所有的迁移文件：
php think migrate:run
运行指定版本的迁移文件：
php think migrate:run -t 20120103083322
回滚迁移：
php think migrate:rollback
```

##路由到操作方法

**提高访问效率**

路由地址的格式为：

>  @[模块/控制器/]操作

 这种方式看起来似乎和第一种是一样的，本质的区别是直接执行某个控制器类的方法，而不需要去解析 模 块/控制器/操作这些，同时也不会去初始化模块。 例如，定义如下路由后：

> 'blog/:id'=>'@index/blog/read'

 系统会直接执行

> Loader::action('index/blog/read');

 相当于直接调用 \app\index\controller\blog类的read方法。

 Blog类定义如下：

> namespace app\index\controller; class Blog { public function read($id){ return 'read:'.$id; } } 

通常这种方式下面，由于没有定义当前模块名、当前控制器名和当前方法名 ，从而导致视图的默认模板规 则失效，所以这种情况下面，如果使用了视图模板渲染，则必须传入明确的参数。 

