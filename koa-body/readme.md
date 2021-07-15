## koa body를 이용한 파일 업로드
koa에서 multipart formdata 를 지원하는 [koa/multer](https://github.com/koajs/multer) 와 같은 여러 모듈이있지만  
여기선 [koa-body](https://github.com/koajs/koa-body)를 사용한다.  

### koa-body 설치
```
npm i koa-body
```

### koa-router와 함께 사용
익스프레스 multer 미들웨어와 똑같이 특정 라우트에 대해서만 사용할수있다.  
일반적으로 koa-router와 함께 파싱이 필요한 라우트에서만 미들웨어 형식으로 사용한다.  
```
const koa=require('koa')
const Router=require('koa-router')
const router=new Router()
const koaBody=require('koa-body')

router.post('/upload',koaBody(),(ctx,next)=>{
  //koa body에서 처리된 file은 ctx.request.files 라는 객체에 저장된다
})

app.use(router.routes())
app.listen(5000)
```
### 옵션
koaBody({}) 에 각종 옵션을 설정할수있다.  
  
body에 대한 리밋을 설정  
* jsonLimit {String|Integer}
* formLimit {String|Integer}
* textLimit {String|Integer}
  
body type 설정  
* json {bool}  
* text {bool}  
* multipart {bool} 멀티파트 바디를 파싱하는여부이며 기본값은 default 이다.  

file 업로드 옵션  
* formidable({})  
koa body는 formidable 패키지로 파일업로드를 처리하는데  
formidable에 전달할 옵션을 쓸수있다.  
자세한 내용은 [node-formidable](https://github.com/node-formidable/formidable#options)에 있다.  
