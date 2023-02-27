# innerText와 textContent의 차이

## innerText

숨겨진 요소의 텍스트는 반환하지 않습니다.

사람이 읽을 수 있는 요소만 처리하죠.

innerText의 값을 읽으면 최신 계산값을 반영하기 위해 리플로우가 발생합니다.

텍스트가 최종적으로 렌더링 된 모습이라고 생각하시면 됩니다.

## textContent

노드의 모든 요소를 반환합니다.

'script'와 'style' 요소를 포함한 모든 요소의 콘텐츠를 가지고 옵니다.

태그와 상관 없이 해당 노드가 가지고 있는 text라고 생각하시면 됩니다.

## 코드로 살펴보기

```HTML
 <p class="greeting">
      Hello
      <span style="display: none">Secret</span>
  </p>
```

```javaScript
console.log(document.querySelector('.greeting').innerText);
//Hello
console.log(document.querySelector('.greeting').textContent);
// Hello
//Secret
```

HTML 코드를 보면 Secret이라는 글자는 display none으로 숨겨져 있습니다.

따라서 화면에서 보면 Hello만 출력될 뿐 Secret은 보이지 않죠.

그러나 javaScript를 통하면 다른 모습을 볼 수 있습니다.

innerText의 경우 숨겨진 Secret의 값을 전혀 읽어오지 못합니다.

반면, textContent의 경우 Secret을 정확히 읽어오는 모습을 볼 수 있습니다.

## 추가

### 🤔 리플로우란?

레이아웃 계산을 다시 하는 것을 말합니다.

HTML 요소의 위치와 크기를 다시 계산해야 하는데, 변경하려는 요소 뿐 아니라 다른 요소까지 다 재계산 해야 합니다.

따라서 리플로우가 자주 발생하는 코드는 지양해야 합니다.

### 🤔 Internet Explorer에서의 innerText

Internet Explorer에서 innerText를 수정하면 요소의 모든 자식 노드를 제거하고, 모든 자손 텍스트 노드를 영구히 파괴해버리는 문제가 있습니다.

### 🤔 리뷰어의 말씀

Q: innerText와 textContent 중 어느것을 더 선호하시나요??

A: 어느 한 쪽에 선호가 있진 않고, 상황에 따라서 다르게 사용하는 것 같습니다.
