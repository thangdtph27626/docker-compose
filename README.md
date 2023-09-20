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

Lệnh này sẽ tạo và khởi động 2 dịch vụ là web và db. Dịch vụ web sẽ sử dụng image nginx:latest và lắng nghe cổng 80. Dịch vụ db sẽ sử dụng image mysql:5.7 và có mật khẩu root là password.

## Một số cấu hình trong docker compose

Trong file docker-compose.yml, chúng ta có thể định nghĩa các cấu hình sau cho các dịch vụ:

image: Chỉ định image Docker mà dịch vụ sẽ sử dụng.
ports: Chỉ định các cổng mà dịch vụ sẽ lắng nghe.
environment: Chỉ định các biến môi trường mà dịch vụ sẽ sử dụng.
volumes: Chỉ định các volume mà dịch vụ sẽ sử dụng.
networks: Chỉ định các mạng mà dịch vụ sẽ sử dụng.
Dưới đây là một số ví dụ về các cấu hình này:

Chỉ định image:

```
YAML
version: '3.8'
services:
  web:
    image: nginx:latest
Vui lòng thận trọng khi sử dụng mã. Tìm hiểu thêm
Chỉ định cổng:
YAML
version: '3.8'
services:
  web:
    image: nginx:latest
    ports:
      - 80:80
Vui lòng thận trọng khi sử dụng mã. Tìm hiểu thêm
Chỉ định biến môi trường:
YAML
version: '3.8'
services:
  web:
    image: nginx:latest
    environment:
      MYSQL_ROOT_PASSWORD: password
Vui lòng thận trọng khi sử dụng mã. Tìm hiểu thêm
Chỉ định volume:
YAML
version: '3.8'
services:
  web:
    image: nginx:latest
    volumes:
      - ./data:/data
Vui lòng thận trọng khi sử dụng mã. Tìm hiểu thêm
Chỉ định mạng:
YAML
version: '3.8'
services:
  web:
    image: nginx:latest
    networks:
      - backend
```


Ngoài lệnh docker-compose up, chúng ta còn có thể sử dụng các lệnh Docker compose sau:

docker-compose down: Dừng và xóa tất cả các dịch vụ được tạo bởi lệnh docker-compose up.
docker-compose build: Tạo image Docker cho các dịch vụ được định nghĩa trong file docker-compose.yml.
docker-compose logs: Xem log của các dịch vụ.
docker-compose ps: Xem trạng thái của các dịch vụ.
docker-compose exec: Chạy một lệnh trong container của dịch vụ.
