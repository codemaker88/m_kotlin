# m_kotlin

## 문제1 - Simple Reactive System

간단한 Reactive 시스템을 구현해봅시다.

Reactive Programing은, 어떤 값이 변경되면, 그 값을 이용하고 있는 곳으로 상태가 전파됩니다.
잘 이해가 안되면, 엑셀의 수식을 생각하면 됩니다.
셀A와 셀B에 정수값이 있을 때, 셀C는 A+B라는 수식의 결과값이라고 가정해봅시다.
이 때, 셀A의 값을 변경하면, 셀 C의 값은 자동으로 변경됩니다.
그래도 잘 이해가 안가면, 이번 기회에 Reactive의 개념을 공부하세요.

https://en.wikipedia.org/wiki/Reactive_programming

알고리즘 문제가 아니고, 설계 문제입니다. 
알고리즘 문제를 푸는것 처럼 접근하면 안됩니다.

이번 문제의 입력과 출력은 아래와 같습니다.

### 입력
행이 하나밖에 없는 엑셀을 가정하면, 배열처럼 보일것입니다.
각각의 인덱스는 알파벳으로 이루어져있고, A~Z 까지입니다.

1. 이 배열은 **정수** 또는 **두개의 값으로 이루어진 사칙연산 수식**으로 이루어져 있습니다. (+ - * /)
2. 각각의 셀은 쉼표로 구분합니다.
3. 수식은 괄호로 묶여있고, 알파벨으로된 인덱스 또는 정수로 이루어집니다. 
4. 이 배열 다음에는 셀의 값이 어떻게 변경되는지가 순서대로 주어집니다.
5. 순환참조는 허용하지 않습니다. (A번째 인덱스의 수식에는 A를 사용하는 식이 들어가지 않는다는 뜻)
6. 값을 계산할 수 없다면(0으로 나누는 경우 등) #err을 출력합니다.

예를 들면, 아래와 같을 것입니다.

```text
100, 20, 3023, (A+E), 10, -30, (D+10), 0, 12345
A=>10
C=>(A*E)
E=>100
```

### 출력
셀의 값이 변경될 때 마다, 영향을 받는 셀의 변경값을 출력합니다.

```text
A=>10 : A=>10, D=>20, G=>30
C=>(A*E) : C=>20
E=>100 : E=>100, D=>110, G=>120
```

### 주의사항
* 기존의 Reactive 라이브러리(Rx등등)을 사용하면 반칙입니다.
* Reactive Programing의 모든 요소를 구현해낼 필요는 없고, Propagation(전파)만 제대로 되면 됩니다.
