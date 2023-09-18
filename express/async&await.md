<h1>async/await란?</h1>
async와 await는 프라미스를 보다 더 쉽게 사용할 수 있도록 해주는 문법이다.<br>
ES2017에 새로 추가된 문법이며, 핵심이라고 할 수 있다.<br>
프로미스의 문제점인 chaining 개선 및 가독성 향상을 위한 문법이다.<br>

```
async function test() {
  try{
      const info = await fetch();
      return info;
     } catch(err) {
  console.log(err)
  }
}
```
와 같이 쓸 수 있다.<br>
async function은 제네레이터로 구현되어 있다.<br>
함수 앞에 async를 붙이게 되면 내부 로직을 제네레이터 함수로 감싸는 것이다.<br>
따라서 async function은 언제나 프라미스를 반환하게 된다.<br>
await는 async function의 yield, next() 기능으로 내부적으로 비동기 역할을 하게 된다.<br>

<h3>아래는 async/await를 사용할 때 주의해야 할 점이다.</h3>
- 비동기 처리를 위해 async/await를 사용하려면 함수 앞에 async를 반드시 붙여 줘야만 내부에서 await이 작동할 수 있다.<br>
- 또한, await는 최상위 레벨 코드(top-level-code)에는 사용할 수 없다.기본적으로는.<br>
- 최상위 레벨 코드에 사용하기 위해서는 익명 async 함수로 코드를 감싸야 한다.<br>
- await가 던진 에러는 try .. catch로 잡는다. try catch가 없다면 프라미스 에러가 일어난다.<br>


