## Props와 State

리액트 컴포넌트에서 다루는 데이터는 두개로 나뉩니다. 바로 props 와 state 인데, 미리 요약하면 props 는 부모 컴포넌트가 자식 컴포넌트에게 주는 값이다. 자식 컴포넌트에서는 props 를 받아오기만하고, 받아온 props 를 직접 수정 할 수 는 없다.

반면에 state 는 컴포넌트 내부에서 선언하며 내부에서 값을 변경 할 수 있다.

# props

props는 property의 약자로, 부모에게 받아온 데이터이다. 리액트의 Data Flow는 단방향 형식으로 부모에서부터 자식으로 이동하기 때문에 거꾸로 올라갈 수 없다. 따라서 props에 있는 데이터들은 수정이 불가능하며 오직 안에있는 값을 꺼내서 사용할수만 있다.

리액트 페이지 문서에 있는 다음 예시를 통해 props 객체를 어떻게 사용하는지 보겠습니다.

```
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

const element = <Welcome name="Sara" />;
ReactDOM.render(
  element,
  document.getElementById('root')
);
```

위의 코드를 보면 element에 Welcome을 담고 있습니다. Welcome은 부모인 element에 있는 Sara를 props에 담아 내려받고 사용하고 있습니다.
