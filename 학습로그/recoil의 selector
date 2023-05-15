# recoil의 selector 왜 쓰고 어떻게 쓰는 걸까?

이번 미션에서는 recoil을 통해 상태관리를 했다.

recoil은 `React를 위한 상태 관리 라이브러리`라는 이름답게 쉽게 적응할 수 있었다.

다만, selector라는 개념은 처음 보았을 때 어떤 상황에서 쓰는 것인지, 왜 쓰는 것인지 와닿지 않았다.

리뷰를 받아 수정하면서 selector에 대한 정리 내용을 써보려 한다.

## selector란?

selector는 atom을 전/후 처리하여 새로운 값을 리턴하거나 기존 atom의 값을 수정할 때 사용한다.

또한, atom의 값이 최신화되면 selector의 값 또한 최신화되어 편하게 사용할 수 있다.

## selector의 사용법은?

```js
const filteredTodoListState = selector({
  key: 'FilteredTodoList',
  get: ({ get }) => {
    const filter = get(todoListFilterState);
    const list = get(todoListState);

    switch (filter) {
      case 'Show Completed':
        return list.filter((item) => item.isComplete);
      case 'Show Uncompleted':
        return list.filter((item) => !item.isComplete);
      default:
        return list;
    }
  },
});
```

공식 문서에 작성된 selector의 모습이다.

여기서 `key`는 selector를 구분할 수 있는 id를 말한다. 고유한 문자열을 가진다.

`get`은 파생된 상태를 반환한다.

get을 통해 다른 atom을 구독할 수 있다.

앞서 atom의 값이 최신화되면 selector의 값이 변한다고 했다.

여기서 해당 atom이 변하면 selector도 변한다는 것이다.

`set`은 쓰기 가능한 상태를 반환한다.

쉽게 말하자면 다른 값으로 변경한다고 보면 된다.

만약 set을 쓰지 않고 get만 사용했다면 Read-only로 사용된다.

## 왜 사용해야 할까?

atom을 직접 변경할 경우 해당 atom을 바라보고 있는 모든 컴포넌트에서 상태가 변경된다.

이에 예상치 못한 부작용이 일어날 수 있다.

selector를 사용하면 atom의 직접 변경하지 않기 때문에 불변성을 유지할 수 있고, 특히 여러 atom을 가공해 사용해야 하는 경우 더욱 유용하다.

또한, selector는 필요한 atom만 구독한다.

따라서 의존성 관리에 효율적이다.

다른 상태 변경으로 인한 재 렌더링을 최소화할 수 있다.

## 이번 미션에서 나는 어떻게 사용했을까?

```js
export const cartProductAtom = atom<CartProduct[]>({
  key: 'cartProductState',
  default: [],
});

export const totalCartProductSelect = selector<number>({
  key: 'totalCartProductState',
  get: ({ get }) => {
    const cartProducts = get(cartProductAtom);

    return cartProducts.length;
  },
});
```

장바구니 상품은 atom으로 묶어두고, 총 상품의 개수를 세는 부분은 selector로 저장했다.

따로 set을 사용할 부분은 없기 때문에 get을 이용해 장바구니 상품 atom을 가져와 그 길이를 return 해 주는 방식으로 사용했다.

이렇게 사용하면 앞서 이야기했듯 atom의 불변성을 유지하면서 전역으로 사용할 수 있다.
