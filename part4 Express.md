# part4 Express 정리
## express 
### 라우팅 :  사용자가 정의한 URL과 method에 따라 해당 로직을 실행하는 것이다.
#### npm install -s exrpess &nbsp;&nbsp;&nbsp; // (npm으로 express 다운)
#### express 표현식 : app.[메소드]('[url]', 처리로직)
### express 사용 이유중 가장 큰 부분은 middleware 를 사용할 수 있기 때문이다.
-----------------------------------------------------------------------------------------------------------
#### const express = require('express') &nbsp;&nbsp;&nbsp; //express 모듈 선언  
#### let app = express(); &nbsp;&nbsp;&nbsp; // express로 만들 서버를 세팅하기 위해 app 변수 선언 및 라우팅, 미들웨어, 에러 처리 로직 선언
#### const http = require('http') &nbsp;&nbsp;&nbsp; // http 서버를 만들기 때문에 http 모듈 선언
#### app.get('/', (req, res, next) => { &nbsp;&nbsp;&nbsp; // 사용자가 GET요청에 '/' 로 접속하면 해당 콜백함수 실행
#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; res.send('hello world'):
#### });
#### http.createServer(app).listen(3000, () => { &nbsp;&nbsp;&nbsp; // routing을 등록한 app의 콜백함수 인자로 (요청 객체, 응답 객체, next 객체) 이다.
#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; console.log('server on : 3000 PORT ')
#### })
#### 응답 객체는 다양한 형태로 응답할 수 있다.
##### 1. send() => 전송된 데이터에 따라서 알맞은 형식으로 바꿔서 전송
##### 2. download() => 해당 파일 다운로드
##### 3. redirect() => 해당 경로로 강제 이동
##### 4. json() => json형태로 데이터를 응답
##### render() , status  &nbsp;&nbsp; etc... 
### http 통신에서는 클라이언트가 포함한 데이터를 사용하기 위해서는 URL을 파싱하여 사용해야 했지만, express에서는 미리 파싱을 해주기 때문에  바로 사용할 수 있어 편리하다(body-parser)
----------------------------------------------------------------------------------------------------------------------
## router
#### 사용 목적 : 복잡한 api를 같은 end-point를 갖고있는 것 끼리 묶어서 복잡한 api를 좀 더 명확하게 구분할 수 있다.
#### const express = require('express')
#### let app = express()
#### const http = require('http')
#### app.use('users/', users)   &nbsp;&nbsp;&nbsp; // end-point가 /users면 users 모듈 호출
#### app.use('boards/', boards)  &nbsp;&nbsp;&nbsp; // end-point가 /boards면 boards 모듈 호출
### 이렇게 router에 따라 해당 모듈로 접근이 안되면 api 한개에 user의 get, post, put, delete board의 get, post, put, delete를 넣어야 하는 상황이 온다
----------------------------------------------------------------------------------------------------------------------
## middleware 란 무엇인가 ?
#### 운영체제와 소프트웨어 응용프로그램 사이에 존재하느 소프트웨어이다. (애매한 표현)
#### 프론트와 백을 연결하여 데이터를 주고 받을 수 있도록 중간에서 매개역할을 하는 소프트웨어이다
#### 미들웨어 중 자주 사용되는 미들웨어는 1. compression(데이터 압축) / 2. body-parser / 3. DB 접속 미들웨어 / 4.multer 등이 있다.
#### vue component에서는 프론트에서 재사용 함수를 저장해 놓은 것이라면, middelware는 client와 server간의 데이터를 주고 받는 과정에서
#### 재사용 할 수 있는 함수를 저장해 놓은 것이라고 이해하면 된다.
#### app.get, app.post, app.put, app.delete 또한 요청 URL과 Method에 따라서 작동하는 미들웨어이다.
#### middleware 표현식 : 
#### app.use((req, res, next) => {  &nbsp;&nbsp;&nbsp; // 미들웨어 등록
#### &nbsp;&nbsp;&nbsp; console.log('첫번째 미들웨어')  &nbsp;&nbsp;&nbsp; // 콘솔창에 '첫번째 미들웨어' 가 표시된다.
#### &nbsp;&nbsp;&nbsp; next()   &nbsp;&nbsp;&nbsp; // 여기서 next() 가 없다면 콘솔창에 표시가 된후,  다음 미들웨어가 실행되지 않아 client는 아무런 응답을 받지 못한다.
#### })
#### app.get((req, res, next) => {  &nbsp;&nbsp;&nbsp; // 미들웨어 등록
#### &nbsp;&nbsp;&nbsp; res.send('hello world') &nbsp;&nbsp;&nbsp; // client는 'hello world' 를 응답받게 된다.
#### })
------------------------------------------------------------------------------------------------------------------------
### Query String이란
#### 사용자가 입력데이터를 전달하는 방법중의 하나로, url 주소에 미리 협의된 데이터를 파라미터를 통해 넘기는 것을 의미한다.
#### 즉, url 뒤에 query prameters( 물음표 뒤에 ooo = ooo 로 연결된 key = value pair부분)을 덧붙여서 추가적인 정보를 서버에 전달하는 것을 의미한다.
#### 클라이언트가 어느 특정 리소스에 접근하고 싶은지를 알 수 있다.
---------------------------------------------------------------------------------------------------------------------


