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

# state

state는 사용자(클라이언트)와 더욱 dynamic 한 통신을 위해 만들어졌습니다. state는 컴포넌트의 특정 상태를 기억하여 화면에 반영하고, 상태가 사용자에 의해 변경되면 다시 화면이 변경되는 기능을 하기위해 존재는 객체입니다.
state 객체를 사용하기 위해서는 부모를 상속받는 class를 생성하여 생성자로 사용해야 합니다.

코드를 통해 예시를 알아보겠습니다.

```
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```

위의 코드를 보면 시간이 변할 때 마다 화면을 업데이트해 주는 코드를 볼 수 있습니다.
이때 시간은 계속해서 변하는 상태 값이기 때문에 state 객체 안에 넣어줌으로써 상태를 관리할 수 있습니다. 이 외에도 onclick 이벤트의 클릭 정보를 저장하거나 하는 등의 방식으로 state를 사용하여 좀 더 많은 기능을 페이지에 추가할 수 있습니다.
