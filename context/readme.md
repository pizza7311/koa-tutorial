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
koa에서는 status와 body 설정으로 오류를 전달할수도있지만  
throw 라는 메소드로 오류를 던질수있으며 기본값은 500으로  
status에 http 상태값과 msg에 문자열 메세지를 전달하며 오류를 쉽게 클라이언트로 던질수있다.  

### ctx 별칭
ctx는 request와 response를 같이 가지고있는 객체이며 ctx.req,ctx.res로 접근하는방법 말고도  
아래의 별칭을 사용하여 바로 접근할수도있다
#### request 별칭
* ctx.header
* ctx.headers
* ctx.method
* ctx.method=
* ctx.url
* ctx.url=
* ctx.originalUrl
* ctx.origin
* ctx.href
* ctx.path
* ctx.path=
* ctx.query
* ctx.query=
* ctx.querystring
* ctx.querystring=
* ctx.host
* ctx.hostname
* ctx.fresh
* ctx.stale
* ctx.socket
* ctx.protocol
* ctx.secure
* ctx.ip
* ctx.ips
* ctx.subdomains
* ctx.is()
* ctx.accepts()
* ctx.acceptsEncodings()
* ctx.acceptsCharsets()
* ctx.acceptsLanguages()
* ctx.get()

#### response 별칭
* ctx.body
* ctx.body=
* ctx.status
* ctx.status=
* ctx.message
* ctx.message=
* ctx.length=
* ctx.length
* ctx.type=
* ctx.type
* ctx.headerSent
* ctx.redirect()
* ctx.attachment()
* ctx.set()
* ctx.append()
* ctx.remove()
* ctx.lastModified=
* ctx.etag=

위의 목록을 예시로 요청주소의 ip를 알아야할때는 ctx.req.ip 또는 ctx.ip 를 입력할수있다.
