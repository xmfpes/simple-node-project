## **Node.js Mongoose를 이용해 MongoDB에 Data Insert**

## STEP 1. DeprecationWarning 제거

```
DeprecationWarning: Mongoose: mpromise (mongoose's default promise library) is deprecated, plug in your own promise library instead: http://mongoosejs.com/docs/promises.html
```
위와 같은 Warning이 발생했었다.

default promise가 deprecate 되었으므로 교체하라는 그런 내용인것 같다.

app.js의 mongoose 모듈을 가져오는 부분 바로 아래 코드에 promise 관련 코드를 추가한다.
```javascript
//var mongoose = require('mongoose');
mongoose.Promise = global.Promise;
```

## STEP 2. products의 리스트를 받아오는 코드 추가

/routes/admin.js의
get, /products 부분의 라우트에서 출력할 리스트를 받아
뷰로 넘겨주는 코드를 작성한다
```javascript
router.get('/products', function(req, res){
    ProductsModel.find(function(err, products){
        res.render('admin/products', 
            { products : products }    
            //ProductModel의 products를 받아서
            //admin/products로 response를 보낸다.
        );
    });
});
```