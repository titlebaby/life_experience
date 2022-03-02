## artisan命令


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