# Part 3
## node.js 에서 웹서버를 만들기 위해 http 모듈 사용
##### const http = require('http');             &nbsp;&nbsp;&nbsp;  // http 모듈을 가져와 사용할 준비
##### &nbsp;&nbsp;&nbsp;http.createServer(function(req,res) {   &nbsp;&nbsp;&nbsp;//createServer는 첫번째 인자로 콜백함수를 받는다. 이 콜백함수는 2개의 인자를 갖는데 (요청객체, 응답객체) 순이다.
##### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     res.writeHead(200);               &nbsp;&nbsp;&nbsp; // 헤더를 만드는 부분 => 응답코드를 200 으로 설정
##### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     res.end('hello world');           &nbsp;&nbsp;&nbsp;   // 서버를 끝내면서 client에게 데이터를 주는 부분
##### }).listen(3000, function() { &nbsp;&nbsp;&nbsp;// listen은 첫번째 인자로 몇번 포트로 설정
#####      &nbsp;&nbsp;&nbsp;console.log('server on : 3000port') 
##### }); 
------------------------------------------------------------------------------------------------------------------------------------------------------------
##### createServer의 콜백함수는 2개의 인자를 갖는데 첫번째가 요청객체, 두번째가 응답객체이다.
##### 서버는 요청 객체에 포함된 '요청 method, URL, 헤더, 요청바디' 를 이용하여 요청사항을 해석한다.
##### 요청바디의 데이터는 바로 가져올 수 없고, 이벤트를 발생해서 데이터를 받아와야 합니다. 
##### 클라이언트가 데이터를 보내면 서버는 데이터 이벤트를 감지하여 데이터를 받아야합니다.
##### req.on('data')를 통해 body를 파싱하고, 파싱이 끝나면 req.on('end')을 실행
##### req.on('data')의 콜백은 클라이언트가 포함한 body 데이터를 인자로 받는데 해당 데이터는 버펴 형태로 toString()을 통해 문자열로 바꿔주어야 한다.
##### 데이터를 처리하는 중에 에러가 발생하면 ----.on('error') 을 호출하면 된다.
##### client에게 응답개체(createServer 콜백의 두번째 인자)를 이용하여 사용자가 원하는 형태로 응답해야한다.
##### 사용자에게 응답시 응답코드를 설정해야 한다  200 : OK / 201 : 새로운 데이터 추가 / 404 : 요청한 리소스 없음 / 500 : 서버의 문제로 에러 발생 이다.
##### res.statusCode = 200;  &nbsp;&nbsp;&nbsp; // 응답객체의 응답코드 설정 
---------------------------------------------------------------------------------------------------------------------------------------------------------------
### 응답객체 - 데이터 전송
##### const http = require ('http')
##### http.createServer( (req,res) => {
##### &nbsp;&nbsp;&nbsp;let resData =<html><body><h3>!!!!hello world!!!!</h3></body></html>
##### &nbsp;&nbsp;&nbsp;res.writeHead(200, {'Content-Type' : 'text/plain'}); &nbsp;&nbsp;&nbsp; // writeHead or setHeader 둘다 사용 가능, content-type또한 데이터에 맞춰서 수정 
##### &nbsp;&nbsp;&nbsp;res.end(resData);
##### }).listen(3000, () => {
##### console.log('server on : 3000port')
##### });
### 데이터 전송
##### const http = require('http')
##### http.createServer( (req, res) => {
##### &nbsp;&nbsp;&nbsp;let {url, headers, method} = req
##### &nbsp;&nbsp;&nbsp; console.log(url, method)
##### &nbsp;&nbsp;&nbsp; res.writeHead(200);
##### &nbsp;&nbsp;&nbsp; res.end('hello world');
##### }).listen(3000, () => 
##### &nbsp;&nbsp;&nbsp; console.log('server on : 3000port')
##### });

