# Xác thực người dùng và phần quyền trong laravel
##1. Middleware
- cơ chế bộ lọc đứng giữa request và response, ví dụ như để kiểm tra xem người dùng xác thực chưa, nếu chưa thì chuyển hướng ko cho đến trang đích nữa.
- tạo middleware mới: `php artisan make:middleware <middleware-name>`
- ví dụ: `<middleware-name>` = `CheckAge` => xuất hiện: app/Http/Middleware/CheckAge.php
- Đăng kí Middleware với hệ thống, có 2 loại middleware, check file  app/Http/Kernel.php để thấy: 
    - `Global middleware` là middleware sẽ được sử dụng với bất kể yêu cầu HTTP đến hệ thống, đơn giản là thêm middleware này vào thuộc tính $middleware trong class app/Http/Kernel.php.
    - `Route middleware` là gắn một middleware với một route xác định, trước khi gắn một route với một middleware phải liệt kê chúng vào thuộc tính $routeMiddleware trong class app/Http/Kernel.php.
    - Ở ví dụ này, ta đăng kí checkAge trong `$routeMiddleware` với tên: `checkage`
- Gán middleware vào route để check xác thực: 
    `
    Route::get('/dashboard', function () {
    //
})->middleware('auth', 'checkage');`
- Ở đây ta sử dụng 2 mdw: auth và checkage vừa tạo 
- có thể truyền tham số vào middleware (thêm biến ở hàm handle), khi đó, tại route, với mdw là `role`, ta truyền giá trị của biến là `superadmin` theo cú pháp: 
`Route::get('/role',[
   'middleware' => 'role:superadmin',
   'uses' => 'MainController@checkRole',
]);
`
- các middleware có thể nhóm thành 1 key duy nhất như `web`, `api`...


