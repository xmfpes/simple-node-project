## **Node.js Template Engine 추가(ejs)**

## STEP 1. ejs 패키지 설치

    npm install --save ejs path

ejs를 설치해, .ejs 템플릿 페이지를 연결해주고,
path를 이용해 해당 경로를 찾아 갈 수 있도록 한다.

## STEP 2. app.js Template Engine 설정 추가

port 설정 바로 아래 부분에 엔진 설정 코드 추가
```javascript
var path = require('path');

var app = express();
var port = 3000;

app.set('views', path.join(__dirname, 'views'));
app.set('view engine', 'ejs');
```

## STEP 3 views 폴더 생성

/views 폴더 생성
/views/admin/products.ejs 파일 생성

테스트를 위하여 products.ejs에 짧은 코드 작성

```html
products
<%= message %>
```

## STEP 4 routes 수정 후 파라미터 전달 확인

routes/admin.js에서 아래의 내용을 수정한다

message에 hello, ejs 메세지를 담아서 products.ejs에서
출력되는지 확인할 것이다.

```javascript
router.get('/products', function(req, res){
    res.render('admin/products', 
        {message : "hello, ejs"}    
    );
});
```

셋팅 후, 아래의 페이지에서 products hello, ejs 라는 메세지가 정상적으로 출력되는지 체크한다.

[localhost:3000/admin/products](localhost:3000/admin/products)
