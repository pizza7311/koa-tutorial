# ctx
koa는 미들웨어의 파라미터로 ctx 객체와 next를 받을수있다.  
ctx는 request와 response를 합쳐놓은 객체이며 ctx.request 와 ctx.response로 접근할수있다  
### cookie
koa에서의 쿠키는 response 객체에서 설정하는것이 아니라 ctx 객체에서 설정한다  
기본적으로 [cookies](https://github.com/pillarjs/cookies) 모듈을 사용한다
### ctx.cookies.get(name,[options])
지정된 이름의 쿠키를 구한다.  
signed 옵션을 사용할수 있으며 서명된 쿠키를 가져올수있다.
### ctx.cookies.set(name,[options])
지정된 이름의 쿠키를 설정한다.  
아래의 옵션들을 지정할수있다.  
* maxAge    쿠키의 만료에 대한 Date.now()의 밀리초를 나타낸 숫자.
* signed    쿠키의 서명 설정
* expiresDate    만료시간
* path      쿠키 경로, 기본값으로 '/'
* domain    쿠키의 도메인
* secure    
* httpOnly 
* overwrite 이전에 설정된 동일한 이름의 쿠키를 덮어씌울지를 설정하는 bool 값

### ctx.throw([status],[msg],[properties])
오류를 던질수있는 메소드로 기본값은 500이며  
status에 http 상태값과 msg에 문자열 메세지를 전달하며 오류를 쉽게 클라이언트로 던질수있다.  
