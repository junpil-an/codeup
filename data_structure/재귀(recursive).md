## 재귀(recursive)

재귀는 자기 자신을 호출 하는 것

#### 재귀함수(recursive function)

자기 자신을 호출하는 함수

```py
arr =[7,3,2,9]

def sum(arr,accu):
  print(arr,accu)
  if (len(arr) ==0): return accu
  last =arr.pop() #뒷 숫자를 빼 accu와 합해준다
  return sum(arr,accu+last) 
```

```python
[7, 3, 2, 9] 0
[7, 3, 2] 9
[7, 3] 11
[7] 14
[] 21
21
```



- 탈출 조건 , 꼭 들어가야 함

```python
def sum(arr,accu):
  if (len(arr) ==0): return sum(arr,accu+arr.pop())
  return sum(arr,accu+arr.pop()) 

sum(arr,0)
```

