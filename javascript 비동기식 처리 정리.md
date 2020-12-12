## 비동기식 프로그램 
### Promise 가 생긴 이유
#### callback 지옥에 빠져 함수의 에러가 어디서 발생한지 찾기 어려워 나온 문법이 Promise 문법이다 
### Promise 정리
### Promise state : pending(실행중인 상태) -> fullfiled(O) or Rejected(X)
#### const promise = new Promise( (resolve, reject) => {
#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;setTimeout( => {
#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // resolve('ellie')
#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // reject(new Error('no network'));
#### &nbsp;&nbsp;&nbsp; }, 2000);
#### });

### Producer의 요청이 성공되었을때 (resolve 되었을 때) then 을 통하여 진행
### Producer의 요청이 실패하였을때 (reject 되었을 때) catch 를 통하여 진행
#### .then(value) => {
#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; console.log(value);
#### }) // ellie 출력됌
#### .catch(error => {
#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; console.log(error);
#### }) // no network 출력됌
#### 즉, resolve의 parameter 값이 then의 parameter로 들어가게 되는 것이다. reject 도 마찬가지이다.
#### 또한 then의 return 타입 또한 promise 타입으로 .catch로 이어질 수 있고 그에 따라 error를 잡을 수 있는 것이다.
#### Promise 객체는 생성되자마자 자동적으로 함수를 실행 하게 된다.
#### 따라서, consumer 가 버튼을 눌럿을때만 사용해야하는 기능이라면 promise로 구현하지 않는 것을 추구한다.
#### 불필요한 네트워크 통신이 발생될 수 있기 때문이다.
##----------------------------------------------------------------------------------------------------------------------------
### async await 정리
#### async 키워드를 함수 앞에 쓰면 코드 블록은 자동으로 promise 형태로 변환이 된다.
#### 또한 await은 async 키워드가 붙은 함수 안에서만 사용 가능하다.
#### 기존 promise 문법과 비교
### Promise 정리
#### const promise = new Promise( (resolve, reject) => {
#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;setTimeout( => {
#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // resolve('ellie')
#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // reject(new Error('no network'));
#### &nbsp;&nbsp;&nbsp; }, 2000);
#### });
###----------------------------------------------------------------------------------------------------------------------------
#### async function fetchuser() {
#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // do network request in 10 secs..
#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return 'ellie';
#### }
### promise에 비하여 async 코드는 보다 간결하고 동기적으로 작동하는 것처럼 보이게 되는 장점이 있다.
### promise에 .then .then 을 하며 연속된 체이닝을 하다보면 코드 가독성이 떨어져 async를 사용하게 되었다.
### await 키워드를 사용할면 promise가 정착 상태가 될때까지 실행을 일시 중지 시킬 수 있다.

