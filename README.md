## 📚 리액트를 다루는 기술

리액트를 다루는 기술 - 김민준

### 1.1 왜 리액트인가

#### 1.1.1 리액트 이해

리액트는 자바스크립트 라이브러리로 사용자 인터페이스를 만드는 데 사용
구조가 MVC, MVW 등인 프레임워크와 달리 오직 V(view)만 신경 쓰는 라이브러리

- 컴포넌트

  - 컴포넌트 : 리액트 프로젝트에서 특정 부분이 어떻게 생길지 정하는 선언체
  - 재사용이 가능한 API로 수많은 기능들을 내장하고 있다
  - 컴포넌트 하나에서 해당 컴포넌트의 생김새와 작동 방식을 정의한다.

- 랜더링
  - 랜더링 : 사용자 화면에 뷰를 보여주는 것
  - 성능을 아끼고 최적의 사용자 경험을 제공하려면 초기 렌더링, 리렌더링 파악해야됨

#### 1.1.1.1 초기 렌더링

- render() {} 함수 : 컴포넌트가 어떻게 생겼는지 정의하는 역할을 한다.

<br>

#### 1.1.1.2 조화 과정(업데이트)

리액트에서 뷰를 업데이트 할 때(데이터에 변화가 있을 때) 우리가 보기에는 변화에 따라 뷰가 변형되는 것처럼 보이지만, 사실은 새로운 요소로 갈아끼우는 것이다.
이 과정도 render() 함수가 한다.
컴포넌트는 데이터를 업데이트 했을 때 단순히 업데이트한 값을 수정하는 것이 아니라, 새로운 데이터를 가지고 render 함수를 호출한다. 그러면 그 데이터를 가진 view가 생성됨
하지만 이때 render 함수가 반환하는 결과를 곧바로 DOM에 반영하지 않고, 이전에 render 함수가 만들었던 컴포넌트 정보와 현재 render 함수가 만든 컴포넌트 정보를 비교한다.
그 후 둘의 차이를 알아내 최소한의 연산으로 DOM 트리를 업데이트 한다.
전체 컴포넌트를 처음부터 다시 렌더링하는 것처럼 보이지만, 사실 최적의 자원을 사용하여 이를 수행하는 것이다.

### 1.2 리액트의 특징

#### 1.2.1 Virtual DOM

리액트의 주요 특징 중 하나는 Virtual DOM을 사용하는 것

<br>

#### 1.2.1.1 DOM이란?

- DOM : 객체로 문서 구조를 표현하는 방법으로 XML이나 HTML로 작성, 트리 형태라서 특정 노드를 찾거나 수정하거나 제거하거나 원하는 곳에 삽입 가능

- DOM의 단점 : 동적 UI에 최적화되어 있지 않다.
  리액트는 Virtual DOM 방식을 사영하여 DOM 업데이트를 추상화함으로써 DOM 처리 횟수를 최소화하고 효율적으로 진행한다.

<br>

#### 1.2.1.2 Virtual DOM

1. 데이터를 업데이트하면 전체 UI를 Virtual Dom에 리렌더링 한다.
2. 이전 Virtual DOM에 있던 내용과 현재 내용을 비교한다.
3. 바뀐 부분만 실제 DOM에 적용한다.

<br>

##### 오해

Virtual DOM을 사용한다고 해서 사용하지 않을 때와 비교하여 무조건 빠른 것은 아니다. 리액트 매뉴얼에는 다음 문장이 있다.

> 우리는 다음 문제를 해결하려고 리액트를 만들었습니다.
> 지속적으로 데이터가 변화하는 대규모 애플리케이션 구축하기

리액트와 Virtual DOM이 언제나 제공할 수 있는 것은 바로 업데이트 처리 간결성이다.
UI를 업데이트 하는 과정에서 생기는 복잡함을 모두 해소하고, 더욱 쉽게 업데이트에 접근할 수 있다.

<br>

#### 1.2.2 기타 특징

리액트는 오직 뷰만 담당한다.
리액트는 프레임워크가 아니라 라이브러리이다.
다른 웹 프레임워크가 Ajax, 라우팅 등과 같은 기능을 내장하고 있는 반면, 리액트는 뷰만 신경 쓰는 라이브러리 이므로 기타 기능은 직접 구현하여 사용해야 한다.
하지만 리액트에는 다른 개발자들이 만든 라이브러리, 예를 들면 axios, fetch, Redux 등이 있기 때문에 필요시 사용하면 된다.
