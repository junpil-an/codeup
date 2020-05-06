## deque() 함수 정리

1. 스택 구현 - **append(),pop()**

```python
from collections import deque
dq = deque('love')
dq
# deque(['l','o','v','e'])
```

2. 큐 구현 - **appendleft(),pop(),append(),popleft()**

```python
dq.append('m')
dq
deque(['l','o','v','e,','m'])
dq.pop()
#'m'
#deque(['l','o','v,','e']) 맨 마지막 데이터가 빠짐
```

3. deque 확장하기 - **extend(),extendleft()**

```python
dq
deque(['l','o','v','e,'])
dq.extend('you')
deque(['l','o','v','e,','y','o','u'])
dq.extendleft('l')
dq
# deque(['l','l','o','v','e,','y','o','u'])
```

4. 리스트 처럼 사용 - insert(), remove()

```python
dq
deque(['l','o','v','e,'])
dq[2]='n'
dq
deque(['l','o','n','e'])
```

```python
dq= deque('love')
dq.insert(0,'K')  #index '0'에 K를 추가 해주면 뒤로 밀려남
dq
deque(['K','l','o','v','e,'])
dq.insert(100,'K') #인덱스 '100'에 K를 추가 100을 넘는 수가없으니 맨 뒤에 추가됨
deque(['K','l','o','v','e,','K'])
dq.remove('K')
deque(['l','o','v','e,','K']) #맨 왼쪽 항목부터 삭제된다 
dq
deque(['l','o','v','e'])

```

5. deque 내용 거꾸로 reverse()

```python
deque['l','o','v','e']
dq.reverse()
dqeue['e','v','o,','l']
```



