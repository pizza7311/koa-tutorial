### 시작하기
```
npm i koa
```
koajs 설치

### koa 애플리케이션
```
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  ctx.body = 'Hello World';
});

app.listen(3000);
```
### 미들웨어
koajs는 express와 비슷하게 미들웨어로 요청을 처리하고  
미들웨어의 파라미터는 ctx와 next를 받을수있으며  
next()를 호출함으로 다음 미들웨어를 호출할수있다  
  
express와 의 차이점은 koa에서의 미들웨어는 순서대로 '다운 스트림'으로 처리를하고  
마지막 미들웨어가 완료되면 다시 '업 스트림' 으로 처음 실행됬던 미들웨어로 되돌아간다  
