# Kiến trúc trong laravel  
## 1. Lifecycle 
## 2. Service container  

- Service container là trái tim của laravel, là thành phần core (cốt lõi) của laravel framework, được dùng rất nhiều nhưng lại không biết dùng ở đâu =))
1. Một số khái niệm cần nằm rõ
- `Denpendency Inversion`: một nguyên lí thiết kế và viết code 
- `Inversion of Control`: Đây là một design partern nằm trong nguyên lý SOLID, nó được tạo ra để tuân thủ theo nguyên lý Denpendency Inversion. Có rất nhiều cách để thực hiện partern này, Dependency Inversion là một trong số những cách đó.
- `Dependency Injection`: Đây là một design partern để thực hiện Inversion of Control. Dependency Injection là cách tổ chức source code, sao cho có thể inject (tiêm) các đối tượng dependency vào trong đối tượng mà nó dependent. Các bạn có thể hiểu đơn giản như này, nếu class A phụ thuộc vào các class khác tức là bên trong class A khởi tạo nhiều đối tượng khác trong đó thì chúng ta có thể truyền những instance của class con đó trong hàm __contruct hoặc hàm setter

2. Service container
- `Service container`, còn được gọi là Inversion of Control Container (trước phiên bản 5), có thể hiểu nôm na là  tấm bản đò, một dịch vụ tổng đài để quản lý class dependency và thực hiện inject class indepent.
- `Service container`: định nghĩa các phương thức bind, resolve, singleton,... và `Service provider` sẽ dùng các phương thức này để thao tác với các service

## 3. Service Providers
- `Service provider`: trung tâm của laravel bootstraping. là trung tâm của việc khởi tạo tất cả các ứng dụng trong Laravel, các thành phần core sẽ được khởi tạo từ Service Provider, Các Service Provider là nơi sẽ thực hiện việc khai báo service và bind vào trong Service Container.
- Chỉ có duy nhất boostrap/app.php thực hiện binding trực tiếp các service, ngoài ra, tất cả đều dc đăng kí tên class để thực hiện binding tong mảng providers trong config/app.php
- tham khảo:
https://viblo.asia/p/laravel-beauty-tim-hieu-ve-service-provider-zb7vDVJnMjKd
https://viblo.asia/p/tim-hieu-service-provider-trong-laravel-bWrZngBrlxw
https://laravel.com/docs/5.5/providers

## 3. Facade
- `Facade` được thiết kế như một cây cầu để người lập trình tiếp cận với "Service" một cách dễ dàng. Bạn có thể sử dụng Facade gần như mọi lúc mọi nơi mà không phải mất công khởi tạo, resolve các instance từ trong Service Container.
- Bản chất của một `Facade` là sử dụng instance của class nào, và nếu khi nào có vấn đề gì cần phải xem code của Framework thì cũng biết được nơi nào để mà tìm. Chẳng hạn như để tìm hiểu về các hàm của Facade `Request` thì bạn nên tìm đến class Illuminate\Http\Request, với Auth thì là Illuminate\Auth\AuthManager hay Mail thì là Illuminate\Mail\Mailer.
- Danh sách các class facade tham chiếu đến: 
https://laravel.com/docs/5.5/facades#facade-class-reference


