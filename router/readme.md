## koa-router
koa는 기본적으로 라우터가 포함되어있지 않으므로 [koa-router](https://github.com/koajs/router) 패키지를 따로 설치하여야한다.  
```
npm i koa-router
```

### Router
익스프레스 라우터와 비슷하게 미들웨어 사용하여 요청을 처리한다.  

```
const Koa = require('koa');
const Router = require('koa-router');

const app = new Koa();
const router = new Router();

router.get('/', (ctx, next) => {
  // ctx.router 객체가 생성된다
});

app.use(router.routes())
```

### 라우팅
/user 주소로 들어오는 요청을 처리하는 라우터 작성하기  
```
...

const Router=require('koa-router')
const user=new Router() //router 객체 생성

user.get('/user',(ctx,next)=>{
  //user 정보를 응답하는 로직...
})

app.use(user.routes())
app.listen(5000)
```

### url 파라미터
1. ctx.params
```
router.get('/user/:id'),(ctx,next)=>{
  // ctx.params 라는 객체가 추가된다
  console.log(ctx.params) // {id:'user_id'}
})
```
2. ctx.query
```
router.get('/user',(ctx,next)=>{  //user?id=12
  //ctx.request.query로 접근하지만 ctx.query로도 접근이 가능하다
  console.log(ctx.query)    //{id:12}
})
```
