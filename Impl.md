

-> mountState 는 통과지점

Impl

```ts

function mountState<S>(
  initialState: (() => S) | S,
): [S, Dispatch<BasicStateAction<S>>] {
  const hook = mountStateImpl(initialState);
  const queue = hook.queue;
  const dispatch: Dispatch<BasicStateAction<S>> = (dispatchSetState.bind(
    null,
    currentlyRenderingFiber,
    queue,
  ): any);
  queue.dispatch = dispatch;
  return [hook.memoizedState, dispatch];
}


```


```ts

count [state, setState] = useState(0);
baseState = 1; // 0 -> 1

setState(state + 1); // baseState를 0 -> 1로 바꾼다.
setState(state + 1); // baseState를 0 -> 1로 바꾼다.

setState(prev => prev + 1); // prev는 baseState를 나타낸다.


```