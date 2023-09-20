# Cách up Docker compose và một số cấu hình trong docker compose

## Cách up Docker compose

Để up Docker compose, chúng ta sử dụng lệnh docker-compose up. Lệnh này sẽ tạo và khởi động tất cả các dịch vụ được định nghĩa trong file docker-compose.yml.

Ví dụ, nếu chúng ta có file docker-compose.yml như sau:

```
YAML
version: '3.8'
services:
  web:
    image: nginx:latest
    ports:
      - 80:80
  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: password
```

Thì chúng ta có thể up Docker compose bằng lệnh sau:

```
docker-compose up
```

Bạn cũng có thể sử dụng các tùy chọn sau với lệnh up:

+  -d: Chạy các service ở chế độ nền.
+ -p: Chỉ định tên của dự án Docker Compose.
+ -f: Chỉ định đường dẫn đến file cấu hình Docker Compose.
+ --build: Xây dựng các image cho các services trước khi khởi động chúng.
+ --no-recreate: Không khởi động lại các services đang chạy.
+ --attach: Gắn kết với đầu ra của các services.

Lệnh này sẽ tạo và khởi động 2 dịch vụ là web và db. Dịch vụ web sẽ sử dụng image nginx:latest và lắng nghe cổng 80. Dịch vụ db sẽ sử dụng image mysql:5.7 và có mật khẩu root là password.

> Lưu ý:

- Nếu bạn đang sử dụng Docker Compose phiên bản 3 hoặc cao hơn, bạn có thể sử dụng lệnh docker compose thay vì docker-compose.
- Nếu bạn đang sử dụng Docker Compose để khởi động nhiều services, các services sẽ được khởi động theo thứ tự phụ thuộc.

## Một số cấu hình trong docker compose


Docker Compose là một công cụ để định nghĩa và chạy nhiều container trên ứng dụng Docker. Nó cho phép bạn tạo một file cấu hình YAML, nơi bạn sẽ định nghĩa các services trên ứng dụng của bạn và định nghĩa tất cả các bước, cấu hình cần thiết để xây dựng các image, up các container và liên kết chúng với nhau.

Dưới đây là một số cấu hình trong Docker Compose mà bạn có thể sử dụng:


- version: Định nghĩa phiên bản của Docker Compose mà bạn đang sử dụng.
- services: Định nghĩa các services cần thiết cho ứng dụng của bạn. Mỗi service có thể là một container, một mạng hoặc một volume.
- build: Định nghĩa cách xây dựng image cho một service.
- image: Định nghĩa image mà bạn muốn sử dụng cho một service.
- ports: Định nghĩa các cổng mà container của bạn sẽ lắng nghe.
- environment: Định nghĩa các biến môi trường cho container của bạn.
- depends_on: Định nghĩa các service mà một service khác phụ thuộc vào.
- networks: Định nghĩa các mạng mà container của bạn sẽ tham gia.
- volumes: Định nghĩa các volume mà container của bạn sẽ sử dụng.


### Cấu hình version

Cấu hình version định nghĩa phiên bản của Docker Compose mà bạn đang sử dụng. Đây là một cấu hình bắt buộc.

Ví dụ:

```
version: '3.9'
```

Cấu hình services

Cấu hình services định nghĩa các services cần thiết cho ứng dụng của bạn. Mỗi service có thể là một container, một mạng hoặc một volume.

Ví dụ:

```
services:
  web:
    image: nginx:latest
    ports:
      - 80:80
  database:
    image: mysql:5.7
```

Trong ví dụ này, chúng ta có hai services: web và database. Service web sử dụng image nginx:latest và lắng nghe trên cổng 80. Service database sử dụng image mysql:5.7.

### Cấu hình build

Cấu hình build định nghĩa cách xây dựng image cho một service. Nếu bạn muốn sử dụng Dockerfile để xây dựng image cho một service, bạn có thể sử dụng cấu hình này.

Ví dụ:

```
services:
  web:
    image: my-image
    build:
      context: .
      dockerfile: Dockerfile
```

Trong ví dụ này, chúng ta sử dụng Dockerfile trong thư mục hiện tại để xây dựng image my-image.

### Cấu hình image

Cấu hình image định nghĩa image mà bạn muốn sử dụng cho một service. Nếu bạn muốn sử dụng image có sẵn, bạn có thể sử dụng cấu hình này.

Ví dụ:

```
services:
  web:
    image: nginx
```

Trong ví dụ này, chúng ta sử dụng image nginx có sẵn.

### Cấu hình ports

Cấu hình ports định nghĩa các cổng mà container của bạn sẽ lắng nghe.

Ví dụ:

```
services:
  web:
    image: nginx
    ports:
      - 80:80
```

Trong ví dụ này, container web sẽ lắng nghe trên cổng 80 của máy chủ.

### Cấu hình environment

Cấu hình environment định nghĩa các biến môi trường cho container của bạn.

Ví dụ:

```
services:
  web:
    image: nginx
    environment:
      - WORDPRESS_DB_HOST=database
      - WORDPRESS_DB_PORT=3306
      - WORDPRESS_DB_NAME=wordpress
      - WORDPRESS_DB_USER=root
      - WORDPRESS_DB_PASSWORD=password
```

Trong ví dụ này, chúng ta định nghĩa các biến môi trường cho container web. Các biến môi trường này sẽ được sử dụng bởi ứng dụng WordPress.

### Cấu hình depends_on

Cấu hình depends_on định nghĩa các service mà một service khác phụ thuộc vào. Service phụ thuộc sẽ được khởi động trước service phụ thuộc vào.

Ví dụ:

```
services:
  web:
    image: nginx
    depends_on:
      - database
```

Trong ví dụ này, service web phụ thuộc vào service database. Service database sẽ được khởi động trước service web.

Cấu hình networks


### Cấu hình networks

Cấu hình networks định nghĩa các mạng mà container của bạn sẽ tham gia. Các mạng này cho phép các container giao tiếp với nhau bằng tên hoặc địa chỉ IP.

Ví dụ:

```
version: '3.9'

services:
  web:
    image: nginx:latest
    networks:
      - my-network

networks:
  my-network:
```

Trong ví dụ này, chúng ta tạo một mạng có tên my-network. Service web sẽ tham gia mạng này.

Các tùy chọn cấu hình networks:

- name: Tên của mạng.
- driver: Trình điều khiển mạng.
- driver_opts: Các tùy chọn cho trình điều khiển mạng.
- external: Tên của mạng bên ngoài.
- labels: Nhãn cho mạng.

### Cấu hình volumes

Cấu hình volumes định nghĩa các volume mà container của bạn sẽ sử dụng. Các volume này cho phép bạn lưu trữ dữ liệu của ứng dụng của bạn độc lập với các container.

Ví dụ:

```
version: '3.9'

services:
  web:
    image: nginx:latest
    volumes:
      - ./data:/var/www/html

volumes:
  data:
```

Trong ví dụ này, chúng ta tạo một volume có tên data. Service web sẽ sử dụng volume này để lưu trữ dữ liệu của ứng dụng.

Các tùy chọn cấu hình volumes:

- name: Tên của volume.
- driver: Trình điều khiển volume.
- driver_opts: Các tùy chọn cho trình điều khiển volume.
- external: Tên của volume bên ngoài.
- labels: Nhãn cho volume.
