## **Node.js Express 프레임워크 사용**

## STEP 1. Express 패키지 다운로드
package.json 생성 및 프로젝트 셋팅

npm init 이후 나오는 설정들은 본인 설정에 맞춘다.

    npm init

express 패키지 설치

    npm install --save express

## STEP 2. app.js 작성

```javascript
var express = require('express');

var app = express();
var port = 3000;


app.get('/', function(req,res){
   res.send('first app');
});

app.listen( port, function(){
   console.log('Express listening on port', port);
});
```

## STEP 3 서버 실행

nodemon은 수정 될 때 마다 서버를 자동으로 재시작 해주기 위해서 추가

로컬이 아닌, global 설정으로 추가(쉘에서 사용하거나 하는 경우는 -g 옵션으로 설치한다고 하는데 약간 헷갈림)

    npm install -global nodemon


npm start 명령어만으로 서버 실행이 가능하도록 package.json에 아래 코드 작성
```javascript
    "scripts": {
    "test": "test",
    "start": "nodemon ./app.js"
  },
```
## STEP 4 라우트 추가

라우트를 추가해주기 위해 routes 폴더 생성
매핑할 이름의 js 파일 생성

admin.js 파일 코드

```javascript
var express = require('express');

var router = express.Router();

router.get('/', function(req, res){
    res.send("admin main page");
});

router.get('/products', function(req, res){
    res.send("admin product page");
});

module.exports = router;
```

수정된 app.js
routes가 추가되었기 때문에, 모듈을 추가해주고 라우트 설정을 추가해준다.

```javascript
var express = require('express')
var app = express();
var port = 3000;

//admin module get
var admin = require('./routes/admin');

app.get('/', function(req, res){
    res.send("Hello, Node.js");
});

//routes add
app.use('/admin', admin);

app.listen(port, function(){
    console.log("server start!");
});
```

셋팅 후, 아래의 페이지가 제대로 동작하는지 확인.

[localhost:3000](localhost:3000)

[localhost:3000/admin](localhost:3000/admin)

[localhost:3000/admin/products](localhost:3000/admin/products)



