# 📘 Table of Contents

- [REST API](#-rest-api)
    - [1. 6 architectural constraints](#6-architectural-constraints)
    - [2. resource naming](#resource-naming)
    - [3. N + 1 Problem](#n+1-problem)
- [JAVASCRIPT](#-javascript)
    - [1. Closures](#closures)
    - [2. Currying](#currying)
    - [3. Hoisting](#hoisting)
    - [4. Destructuring](#destructuring)
    - [5. Rest Parameters](#rest-parameters)
    - [6. Spread](#spread)
- [Docker](#-Docker)
- [Nginx](#-nginx)

## 📘 REST API
### 6 architectural constraints
1. Uniform interface
2. Client–server
3. Stateless
4. Cacheable
    - Expires
      ```
      Expires: Thu, 03 Dec 2020 23:02:37 GMT
      ```
    - Cache-Control
      ```
      Cache-Control: max-age=3600
      ```
    - Last-Modified
      ```
      Last-Modified: Mon, 07 Dec 2020 16:21:06 GMT
      ```
    - ETag
      ```
      ETag: "abcd1234567n34jv"
      ```
      [Read more](https://itplusx.info/restful-api-phan3-caching/)
5. Layered system
6. Code on demand (optional)

[Read more](https://restfulapi.net/rest-architectural-constraints/)

### Resource naming
1. document
2. collection
3. store
4. controller

[Read more](https://restfulapi.net/resource-naming/)

### N+1 Problem

>The idea is that insufficient information in collection resources may lead to the N+1 problem in REST APIs

> when you fetch parent and fectch N children

## 📘 Javascript
### Closures
> Closure là một chức năng có quyền truy cập vào phạm vi cha, ngay cả sau khi scope đã đóng.

```
function speak() {
  var words = 'hi';
  return function logIt() {
    console.log(words);
  }
}

var sayHello = speak();
sayHello()
```

[Read more](https://anonystick.com/blog-developer/discuss-about-closures-in-javascript-2019051695927961.jsx)

### Currying

#### ES5

``` 
var add =   function (a){
    return function(b){
        return function(c){
            return a+b+c;
         }        
    }
}
console.log(add(2)(3)(4)); //output 9
console.log(add(3)(4)(5)); //output 12
```

#### ES6

```
const add = (a, b) => a + b

add(1, 2) //should return 3

--------------------------

const add = a => b => a + b

add(1)(2) //should return 3
```

[Read more](https://anonystick.com/blog-developer/javascript-currying-in-javascript-2019050935248071)

### Hoisting

 > Khi một file javascript compiled bởi browser, nhưng trước khi nó thực sự executed thì Function declaration sẽ được stored in memory và được đẩy lên nhưng chính xác ta vẫn nhìn nó vẫn ở vị trí cũ. Và khi javascript file thực sự run thì browser thực sự đã biết những function đó trước khi đọc code của file javascript. 

```
// Function declaration
function add(num1, num2) {
	return num1 + num2;
}

// Function expression
var add = function (num1, num2) {
	return num1 + num2;
};

```

#### How function declaration work

```
var salary = "1000$";

(function () {
  console.log("Original salary was " + salary);

  var salary = "5000$";

  console.log("My New Salary " + salary);
})();

Output:
  Original salary was undefined
  My New Salary 5000$

```

```

var salary = "1000$";

(function () {
  var salary = undefined;
  console.log("Original salary was " + salary);

  salary = "5000$";

  console.log("My New Salary " + salary);
})();

```


[Read more](https://anonystick.com/blog-developer/hoisting-javascript-la-gi-hoisting-tot-hay-xau-chi-can-1-phut-de-hieu-2020051681168206)

### Destructuring

> Allow set variables of Object or Array reduce line of code

- Destructuring Objects
  ```
  const person = {
    name: 'giang',
    age: 25
  }

  //original methods
  const name = person.name
  const age = person.age

  //destructuring
  const { name, age } = giang
  ```
- Destructuring Array
  ```
  const date = ['1996', '03', '08']
  
  //original methods
  const year = date[0]
  const month = date[1]
  const day = date[2]

  //destructuring
  const [year, month, day] = date
  ```
### Rest Parameters

> using when unspecifed parametr

- Rest
  ```
  function restTest(...args) {
    console.log(args)
  }
  restTest(1, 2, 3, 4, 5, 6);// [1, 2, 3, 4, 5, 6]
  ```

### Spread

> Can copy object, update object, merged array ...

- Copy object
  ```
  const person = {
    name: 'giang',
    age: 25
  }

  const p = person;
  p.name = 'test'

  console.log(person.name) //output: test
  console.log(b.name) //output: test
  ```

  ```
  const person = {
    name: 'giang',
    age: 25
  }

  const p = {...person};
  p.name = 'test'

  console.log(person.name) //output: giang
  console.log(b.name) //output: test
  ```
- Merged array
  ```
  const arr = [🤷‍♂️,👀,🐱‍🚀]
  const arr1 = [🐱‍🏍,🐱‍👤]

  const mergedArray = [...arr,...arr1]
  //mergedArray: [🤷‍♂️,👀,🐱‍🚀,🐱‍🏍,🐱‍👤] 
  ```  

## 📘 Docker
- Dockerfile build image -> run conatiner from image

1. Dockerfile
2. Docker-compose
3. Docker build
4. images

## 📘 Nginx
> Webserver kiến trúc hướng sự kiện (event-driven) không đồng bộ (asynchronous)

> Tuy nhiên, NGINX hoạt động theo kiến trúc bất đồng bộ (asynchronous) hướng sự kiện (event driven). Nó cho phép các threads tương đồng được quản lý trong một tiến process. Mỗi process hoạt động sẽ bao gồm các thực thể nhỏ hơn, gọi là worker connections dùng để xử lý tất cả threads.

> Worker connections sẽ gửi các yêu cầu cho worker process, worker process sẽ gửi nó tới master process, và master process sẽ trả lời các yêu cầu đó. Đó là lý do vì sao một worker connection có thể xử lý đến 1024 yêu cầu tương tự nhau. Nhờ vậy, NGINX có thể xử lý hàng ngàn yêu cầu khác nhau cùng một lúc.

#### Some feature of Nginx
1. Can hanlde 10000 request at the same time
2. Static file
3. Proxy
4. Rewrite url
5. limit connection
6. support websocket
7. support flv and mp4

[Read more](https://wiki.matbao.net/nginx-la-gi-huong-dan-kiem-tra-va-cai-dat-nginx-server/)
