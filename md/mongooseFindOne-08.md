## **Node.js Mongoose를 이용해 Detail 페이지 제작하기(findOne)**

## STEP 1. API 작성
/routes/admin.js 파일에 routes 추가

```javascript
router.get('/products/detail/:id' , function(req, res){
    //url 에서 변수 값을 받아올떈 req.params.id 로 받아온다
    ProductsModel.findOne( { 'id' :  req.params.id } , function(err ,product){
        res.render('admin/productsDetail', { product: product });  
    });
});
```
## STEP 2. detail view 파일 작성
```html
<% include ../includes/header.ejs %>

    <div class="panel panel-default">
        <div class="panel-heading">
            <%=product.name%>
        </div>
        <div class="panel-body">
            <div style="padding-bottom: 10px">
                작성일 : 
                <%=product.getDate.year%> - 
                <%=product.getDate.month%> - 
                <%=product.getDate.day%>
            </div>
            <%=product.description%>
        </div>
    </div>
 
    <a href="/admin/products" class="btn btn-default">목록으로</a>
    <a href="/admin/products/edit/<%=product.id%>" class="btn btn-primary">수정</a>

<% include ../includes/footer.ejs %>
```

글 리스트에서 해당 글을 클릭했을 경우, 해당 글의 상세페이지를 보여주는지를 체크한다.