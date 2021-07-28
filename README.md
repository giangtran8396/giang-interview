# 📘 Table of Contents

- [REST API](#-rest-api)
    - [1. 6 architectural constraints](#6-architectural-constraints)
    - [2. resource naming](#-resource-naming)
- [JAVASCRIPT](#-javascript)
    - [1. Closures](#closures)
    - [2. Currying](#currying)
    - [3. Hoisting](#hoisting)
- [Docker](#-Docker)
- [Nginx](#-nginx)

## 📘 REST API
### 6 architectural constraints
1. Uniform interface
2. Client–server
3. Stateless
4. Cacheable
5. Layered system
6. Code on demand (optional)

[Read more](https://restfulapi.net/rest-architectural-constraints/)

### Resource naming
1. document
2. collection
3. store
4. controller

[Read more](https://restfulapi.net/resource-naming/)

## 📘 Javascript
### Closures
- Closure là một chức năng có quyền truy cập vào phạm vi cha, ngay cả sau khi scope đã đóng.

[Read more](https://anonystick.com/blog-developer/discuss-about-closures-in-javascript-2019051695927961.jsx)

### Currying

[Read more](https://anonystick.com/blog-developer/javascript-currying-in-javascript-2019050935248071)

### Hoisting

[Read more](https://anonystick.com/blog-developer/hoisting-javascript-la-gi-hoisting-tot-hay-xau-chi-can-1-phut-de-hieu-2020051681168206)

## 📘 Docker
- Dockerfile build image -> run conatiner from image

1. Dockerfile
2. Docker-compose
3. Docker build
4. images

## 📘 Nginx
- Webserver kiến trúc hướng sự kiện (event-driven) không đồng bộ (asynchronous)
- Tuy nhiên, NGINX hoạt động theo kiến trúc bất đồng bộ (asynchronous) hướng sự kiện (event driven). Nó cho phép các threads tương đồng được quản lý trong một tiến process. Mỗi process hoạt động sẽ bao gồm các thực thể nhỏ hơn, gọi là worker connections dùng để xử lý tất cả threads.
- Worker connections sẽ gửi các yêu cầu cho worker process, worker process sẽ gửi nó tới master process, và master process sẽ trả lời các yêu cầu đó. Đó là lý do vì sao một worker connection có thể xử lý đến 1024 yêu cầu tương tự nhau. Nhờ vậy, NGINX có thể xử lý hàng ngàn yêu cầu khác nhau cùng một lúc.
1. Can hanlde 10000 request at the same time
2. Static file
3. Proxy
4. Rewrite url
5. limit connection
6. support websocket
7. support flv and mp4

[Read more](https://wiki.matbao.net/nginx-la-gi-huong-dan-kiem-tra-va-cai-dat-nginx-server/)
