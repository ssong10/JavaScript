* 이벤트 루프 : call stack, callback queue 확인
    * call stack 이 비어있으면, callback queue 에서 call stack으로 이동
    * 이벤트(함수 실행..)
    * tick(틱)
    > setTimeout 과 관련하여 시험에 나옴 .

```javascripts
function a() {
    console.log('a')
}
console.log('hi')
setTimeout(a, 3000)
console.log('bye')
```

* synchronous / Asynchronous
* blocking / non-blocking