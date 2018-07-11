## RESTful

| 请求类型 | 路由规则         | 对应操作方法      | 描述         |
| -------- | ---------------- | ----------------- | ------------ |
| GET      | `blogs`          | index/Blog/index  | 显示博客列表 |
| GET      | `blogs/create`   | index/Blog/create | 新增博客页面 |
| POST     | `blogs`          | index/Blog/save   | 保存博客内容 |
| GET      | `blogs/:id`      | index/Blog/read   | 查看博客内容 |
| GET      | `blogs/:id/edit` | index/Blog/edit   | 编辑博客页面 |
| PUT      | `blogs/:id`      | index/Blog/update | 更新博客内容 |
| DELETE   | `blogs/:id`      | index/Blog/delete | 删除博客     |

