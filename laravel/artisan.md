# artisan命令
## make:controller/model

```php
## 创建-资源控制器
php artisan make:controller BlogController --resource

Route::resource('blogs', 'BlogController'); //单个资源路由

Route::resources([
    'blogs'     => 'BlogController',
    'comments'  => 'CommentController'
]);



## 查看已生成的路由
php artisan route:list

## 资源控制器还有一种不需要 HTML 页面方法的API 路由，只提供数据接口。
php artisan make:controller CommentController --api
Route::apiResource('comments', 'CommentController');

## 资源嵌套，是指两个控制类，通过路由绑定在一起。？？
why ？？ 不懂用法。


## 创建模型
php artisan make:model Http/Models/User
php artisan make:model Models/User

## 创建控制器和模型？？生成单元栏？
php artisan admin:make CrowdfundingProductsController --model=App\\Models\\Product


```


```sql
## mysql5.7+ 支持json查询
select * from `laravel_users` where json_unquote((`list`, '$."id"')json_extract) = ?（？？）

## exists 实现子查询的深入理解？？？
select * from `laravel_users` where exists (
    select 1 from `laravel_books` 
    where laravel_books.user_id = laravel_users.id
)

## select 1 from，一般用于子查询的手段，目的是减少开销，提升效率

```

## 菜单做了调整
```
php artisan admin:export-seed
```

## 创建request类
```
php artisan make:request CrowdFundingOrderRequest

```

## 创建数据库迁移文件
```
## 为以有的表orders添加type字段的迁移文件
php artisan make:migration orders_add_type --table=orders

```
## 执行文件迁移
```
$ php artisan migrate
```

## 创建授权策略

```
php artisan make:policy PostPolicy 
```

## 创建监听事件
```
php artisan make:listener UpdateCrowdfundingProductProgress --event=OrderPaid

## 注册一下事件与监听器的关系
## 触发事件
```

## 队列
```
# 启动一个队列处理器
php artisan queue:work
# 创建队列任务
php artisan make:job SendReminderEmail
# 

```

## 生成 配置文件
```
composer require laravel/scout
## 发布
php artisan vendor:publish --provider="Laravel\Scout\ScoutServiceProvider"
```

## 导出后台数据库
```sql
php artisan admin:export-seed
## 登录
mysql -uroot -p laravel-shop
## 导出数据库数据到文件
mysql> select email,min(user_addresses.id),'password' FROM `users` join user_addresses on users.id=user_addresses.user_id group by email into outfile '/var/lib/mysql-files/users.csv' FIELDS TERMINATED BY ',' ENCLOSED BY '"' LINES TERMINATED BY '\n';
```

##  创建 Request 类
```
php artisan make:request SeckillOrderRequest
```