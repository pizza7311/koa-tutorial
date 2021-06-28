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
마지막 미들웨어가 완료되면 응답이 끝나더라도 다시 '업 스트림' 으로 처음 실행됬던 미들웨어로 되돌아간다  
아래의 예제는 `위에서 아래로 실행되었다가 다시 위로 올라가는 순서로 동작한다`

```
const Koa = require('koa');
const app = new Koa();

// 로깅 미들웨어

app.use(async (ctx, next) => {
  await next();    //1. 바로 다음 미들웨어를 호출하고있다
  const rt = ctx.response.get('X-Response-Time');     //5. 두번째 미들웨어에서 설정했던 X-Response-Time을 가져와 출력한다
  console.log(`${ctx.method} ${ctx.url} - ${rt}`);
});

app.use(async (ctx, next) => {
  const start = Date.now();      //2. start 라는 변수에 시작시간을 저장하고 바로 다음미들웨어를 호출했다
  await next();
  const ms = Date.now() - start;     //4. 현재시간을 구한다음 start를변수를 뺀뒤 ctx에 X-Response-Time 이라는 변수로 설정했다
  ctx.set('X-Response-Time', `${ms}ms`);
});

// 응답

app.use(async ctx => {
  ctx.body = 'Hello World';         //3. 여기서 응답이 끝나면 다시 위로 되돌아간다
});

app.listen(3000);
```
