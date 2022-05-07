## styled components

---

### styled components란?

**_styled components_**는 `javascript`에서 `css`를 사용 할 수 있도록 도와주는 **_스타일링 프레임 워크_** 이다. `React Component`에 특정 스타일링을 할 수 있기 때문에 재사용성을 더 높일 수 있고, `javascript`에 영향을 받는 스타일링을 간편하게 구현 할 수 있다.

```java script
import styled from "styled-components";

styled.button`
  font-size: 1rem;
`;
```

예를 들어, 다음과 같이 Styled Components로 작성된 JavaScript 코드는 아래 CSS 코드가 적용된 `<button>` HTML 엘리먼트를 만들어낸다.

```CSS
button {
  font-size: 1rem;
}
```

이런 식으로 Styled Components를 이용해서 JavaScript 코드 안에 삽입된 CSS 코드는 글로벌 네임 스페이스를 사용하지 않는다. 다시 말해, 각 JavaScript 파일마다 고유한 CSS 네임 스페이스를 부여해주기 때문에, 각 React 컴포넌트에 완전히 격리된 스타일을 적용할 수 있게 된다.

이 것은 순수하게 CSS만을 사용했을 때는 누리기 어려웠던 대표적인 CSS in JS의 장점 중 하나이다.
