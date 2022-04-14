## Debugging

**defining the problem**

- 예상하는, 원하는 문제나 목표를 정확하게 정의
- 지금 일어나고 있는 일은 무엇인지, 어떤 순서로 어떻게 버그나 이슈가 발생하고 있는지 정의

이 둘의 차이를 메꿔나가는 과정

- UX, UI
- login, flow
- performance

디버깅 뿐만아니라 아래처럼 다양한 방법을 이용할 수 있다

- unit testing
- integration testing
- control flow analysis
- log file aalysis, print logs
- interactive debugging
- memory dumps (메모리 사용량 확인)
- profiling (CPU나 여러가지 성능 프로파일링)

---

vscode에서 run and debug 탭에 와서 브라우저인지 노드용인지 선택

확인하고 싶은 곳(의심가는 곳)에서 브레이크 포인트 설정

왼쪽

- variables에는 local, global 변수 확인 가능
- watch에서는 + 아이콘 이용해서 관심있는 단어나 문장을 검색해서 확인가능
- 콜스택에서 함수실행 순서 확인

## 인터랙티브 디버깅

variables에서 값을 내가 지정할 수 있다(그리고 watch에서 확인가능) 동적으로 변경
예) i를 3으로 줬을 때 -> num의 값은 뭐지? -> watch에서 확인

## 브레이크 포인트 오른쪽 마우스 -> edit Breakpoint

특정한 조건을 만족할 때만 브레이크 포인트가 동작할 수 있도록 할 수 있다
예) i === 5, 이렇게 조건문 작성하고 그 조건에 해당될때만 브레이크포인트 걸림

---

# console 100% 활용하기

1. log level

```
console.log('obj');  // 개발 - 출력 (배포단계에선 삭제)
console.info('obj');  // 정보 (배보단계에서 되도록 삭제, 정말 중요하면 남겨둠)
console.warn('obj'); //  경보 (심각한 건 아님)
console.error('obj'); //  에러! 예상하지 못한 에러, 시스템 에러
```

2. assert // 조건이 거짓일 때만 출력

```
console.assert(2 === 3, 'not same!');
console.assert(2 === 2, 'same!');
```

3. print object

```
console.table('obj');  // 가독성 있게 테이블로 출력
console.dir('obj', {colors: false, depth: 1});
// 옵션을 전달할 수 있고 오브젝트 안에 또다른 오브젝트가 있다면
얼마나 자세히 깊이 표현할건지 정해서 출력가능
(color란 오브젝트는 출력안되고, 깊이는 단 하나의 오브젝트만 출력)
```

4. measuring time

```
console.time('for loop');  // 여기서부터 시작해서
for (let i = 0; i < 10; i++>) {
  i++;
}
console.timeEnd('for loop'); // 이것이 출력될 때까지 걸린 시간
```

5. counting

```
function cat() {
  console.count('cat function');
}
cat();  // cat function: 1
cat();  // cat function: 2
cat();  // cat function: 3  이라고 출력된다

초기화하려면?
console.countReset('cat function');
cat(); // cat function: 1
```

6. trace

```
function f1() {
  f2();
}
function f2() {
  f3();
}
function f3() {
  console.trace();  // 어떤 파일, 몇번째 줄에서 실행되었는지도 알 수 있다
  console.log('hi! 🎃');
}
f1();
```

배포할 때엔 삭제해야할 거 꼭 삭제하고!
