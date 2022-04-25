# immer.js란?

react에서 불변성을 유지하는 코드를 작성하기 쉽게 해주는 라이브러리.

# 불변성이란?

쉽게 말하면 상태를 변경하지 않는 것이다
상태를 변경하는데, 상태를 변경하지 않으면서 원하는 상태를 바꾼다는게 어불성설이지만 react가 어떻게 컴포넌트를 유지하는지(기본 속성) 알면 왜 저런 말이 나오는지 이해하게 된다

# react 기본 속성

react는 기본적으로 부모 컴포넌트가 리렌더링을 하면 자식 컴포넌트도 리렌더링하게 된다.즉, 얕은 비교를 통해 새로운 값인지 아닌지를 판단한 후 새로운 값인 경우 리렌더링을 하게 된다.
여기서 얕은 비교란 간단히 말하자면 객체, 배열, 함수와 같은 참조 타입들을 실제 내부 값까지 비교하지 않고 동일 참조인지(동일한 메모리 값을 사용하는지)를 비교하는 것을 뜻한다.

state가 얕은 비교를 통해 컴포넌트가 리렌더링 된다는 말은 굉장한 의미가 있다. 아래의 시나리오를 보면 왜 react에서 요소를 직접 변경하면 안되는지 알 수 있다.
우리가 컴포넌트를 리렌더링 해야하는 상황이 있다고 가정하고, 타입이 배열인 state를 바꾼다.
이때, state.push(1)을 통해 state 배열에 직접 접근하여 요소를 추가한다.
우리는 push 전과 다른 값이라고 생각하지만, 리엑트는 state라는 값은 새로운 참조값이 아니기 때문에 이전과 같은 값이라고 인식하고 리렌더링 하지 않는다.
즉, 위 이유로 우리가 state를 바꾸고 돔을 다시 만들려면, 새로운 객체 or 배열을 만들어 새로운 참조값을 만들고, react에게 이 값은 이전과 다른 참조값임을 알려야하는 것이다.
위 과정은 가상 dom에서만 이뤄지는 렌더링이며, 렌더링을 마치면 react의 비교 알고리즘에 의해 변화가 일어난 컴포넌트만 실제로 업데이트되어 우리 눈에 보이게 되는 것이다.

# 불변성 지키면서 state 바꾸기

위에서 왜 불변성을 react에서 지켜야하는지 알아보았습니다.
그리고, 이제 그 불변성을 지키면서 state를 바꿔보도록 합시다

# 배열에 추가

setUsers(state.array.concat(user));

        Copied!

# 배열에서 삭제

const onRemove = id => {
// user.id 가 id 인 것을 제거
setUsers(users.filter(user => user.id !== id));
};

        Copied!

# 배열에서 수정

const onToggle = id => {
setUsers(
users.map(user =>
user.id === id ? { ...user, active: !user.active } : user
)
);
};

        Copied!

# 객체에서 추가

setState(state => {...state, key: value})

        Copied!

# 객체에서 제거

setState(state => {...\_.omit(state, 'deleteKey')})

        Copied!

# 객체에서 수정

setState(state => {...state, key: newValue})

        Copied!

위처럼 배열 혹은 객체를 바꾸면 불변성을 유지하면서 변경이 가능합니다, 그러나 immer.js를 이용하면 일반 객체 또는 배열을 다루듯 사용하면 immer가 불변성을 유지시켜줍니다.
#immer
import produce from "immer";

const baseState = [
{
todo: "Learn typescript",
done: true
},
{
todo: "Try immer",
done: false
}
];

const nextState = produce(baseState, draftState => {
draftState.push({ todo: "Tweet about it" });
draftState[1].done = true;
});

        Copied!

immer에서 우리가 쓸 함수는 오직 produce만 알면 됩니다. 2가지의 파람을 가져오고 첫번째는 수정하고 싶은 객체/배열, 두번째는 첫번째 파라미터에 할당된 객체/배열을 바꾸는 함수입니다.
