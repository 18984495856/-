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

