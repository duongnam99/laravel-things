# Quy trình với Database và CRUD trong laravel
## Eloquent  

1. Many to many  

    - Tên class model là tên bảng bỏ `s`, bảng `shops` => chạy `php artisan make:model Shop -m` (tạo luôn migration). tương tự với bảng còn lại (eg: `products`). Bảng trung gian ko cần model
    - Để xác đinh tên bảng trung gian, Laravel sẽ ghép bằng tên 2 model theo thứ tự  bảng chữ cái => có bảng pivot: `product_shop`. => Tạo migration `php artisan make:migration create_product_shop_table`, tương tự với 2 bảng chính.
    - Trong mỗi Model (class), tạo phương thức kết nối, ví dụ, trong model Shop, tạo phương thức `products`:
    `  public function products()
    {
    	return $this->belongstoMany('App\Product','tên bảng trung gian: `product_shop`', 'khóa ngoại của bảng tạo quan hệ: `shop_id`, 'khóa ngoại của bảng quan hệ đến: `product_id`');
    }
    `
    - Các thông số 2,3,4 của phương thức trên nếu tuân thủ theo nguyên tắc đặt tên, sẽ ko cần có.
    - Thêm: 
    `
    $user = App\User::find(1);
    $user->roles()->attach($roleId);
    `
    Xóa: `detach`