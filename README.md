# React Part1
CDN : https://ko.reactjs.org/docs/cdn-links.html
```js
<script crossorigin src="https://unpkg.com/react@17/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script type="text/babel">

</script>
```
## 개발 환경 
1. Node.js
    - nvm 사용.
1. Browser
1. Git
1. VSCode

## React 라이브러리
1. react-dom  
리액트 컴포턴트 와 HTMLElement 연결하기  
https://ko.reactjs.org/docs/react-dom.html
1. react  
리액트 컴포넌트 만들기  
https://ko.reactjs.org/docs/react-api.html

## React 컴포넌트
Class or 함수 React 컴포넌트 사용.
```js
//Class 리액트 정의
class ClassComponent extends React.Component{
  render(){
    return <div>Hellow</div>
  }
}
//사용
ReactDOM.render(<ClassComponent />,document.querySelector('#root'))
```
```js
//함수 리액트 정의
function FunctionComponent(){
  return <div>Hellow Funcion</div>
}
//화살 함수
const FunciotnComponent2 = () => <div>Hello22</div>

//사용
ReactDOM.render(<FunctionComponent />,document.querySelector('#root')
```
### React.createElement 컴포넌트 만들기
```js
React.createElement(
  type, //HTML 태그 이름 문자열 | 리액트 컴포넌트 | React.Fragment
  [props],// 리액트 컴포넌트에 넣어주는 데이터 객체 ex)class / id 등 옵션
  [...children] //자식으로 넣어주는 요소들 //ex) <h1>children</h1>
)
```
### Fragments
React에서 컴포넌트가 여러 엘리먼트를 반환하는 것은 흔한 패턴입니다. Fragments는 DOM에 별도의 노드를 추가하지 않고 여러 자식을 그룹화할 수 있음.
```js
  ReactDOM.render(
    React.createElement(
      React.Fragment,
      null,
      `type 이 "리액트 Fragment" 입니당.`
    ),
    document.querySelector('#root')
  )
  //==><div id="root">type 이 "리액트 Fragment" 입니당.</div>
```
### JSX
React.createElement 에 비해 가독성이 뛰어남.
babel과 같은 컴파일 과정에서 문법적 오류를 인지하기 쉬움  
문법
- 최상위 요소는 하나여야 한다.
- 최상위 요소를 리턴하는 경우 ()로 감싸야 한다.
- 자식들을 바로 랜더링하고싶으면 <>자식들</>를 사용 => Fragment
- 자바스크립트 표현식을 사용하려면, {표현식} 를 이용합니다.
- if 문은 사용할 수 없으며 삼항 연상자 혹은 &&(논리연산자)를 사용
- style 을 이용해 인라인 스타일링이 가능합니다.
- class 대신 className 을 사용해 class 를 적용할 수 있습니다.
- 자식요소가 있으면, 꼭 닫아야 하고,(`<p>어쩌구</p>`) 자식요소가 없으면 열면서 닫아야(`<br />`) 한다
  
### Props or State
Props: 컴포넌트 외부에서 컴포넌트에게 주는 데이터
State(개체 형태로): 컴포넌트 내부에서 변경할 수 있는 데이터
둘 다 변경이 발생하면, 랜더링이 다시 일어날 수 있음.

### Event Handling
JSX에 이벤트를 설정할 수 있음.
- camelCase 로만 사용할 수 있습니다. ex)onClick, onMouseEnter
- 이벤트에 연결된 자바스크립트 코드는 함수 (이벤트={함수} 와 같이 사용)  
  ex) onClick={()=>{console.log('123')}}
- 실제 DOM 요소들에만 사용 가능(리액트 컴포넌트에 사용하면, 그냥 props 로 전달)
```js
class Comp extends React.Component {
  render() {
    return (
      <div>
        <button onClick={() => {
          console.log('clicked');
        }}>클릭</button>
      </div>
    );
  }
}
```

## Component Lifecycle
리액트 컴포넌트는 탄생부터 죽음까지 여러지점에서 개발자가 작업이 가능하도록 메소드를 오버라이딩 할 수 있게 해준다.

<img src="https://media.slid.es/uploads/640576/images/4505412/1_sn-ftowp0_VVRbeUAFECMA.png" alt="" height="450" width="1000">   
