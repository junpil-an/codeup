# Class

```python
result =0

def add(num):
    global result
    result +=num
    return result

print(add(3))
print(add(4))

# 3과 7이 출력
```

2대의 계산기가 필요한 상황이 발생하면 어떻게 해야 할까, 각각의 결과값을 유지하기 위해 add함수 하나만으로는 따로 유지할 수 없다

```python
result1 = 0
result2 = 0

def add1(num):
    global result1
    result1 += num
    return result1

def add2(num):
    global result2
    result2 += num
    return result2

print(add1(3))
print(add1(4))
print(add2(3))
print(add2(7))
# 3 7 3 10 출력
```

result1 의 결과값이 2에 아무 영향을 끼치지 않음을 알 수 있음, 하지만 계산기가 3개

5개, 10개로 점점 더 많이 필요해진다면 어떻게 해야 할까, 전역 변수와 함수를 추가할 것인가?, 상황은 점점 더 어려워 질 것이다

```python
class Calculator:
    def __init__(self):
        self.result=0
    def add(self,num):
        self.result +=num
        return self.result

call = Calculator()
call2 = Calculator()

print(call.add(3))
print(call.add(4))
print(call2.add(3))
print(call2.add(7))

# 3 7 3 10
```

Calculator 클래스로 만든 별개의 계산기( 객체) 가 각각의 역할을 수행한다,result개수가 늘어나도 객체만 생성하면 되기때문에 매우 간단해 진다.

```python
def sub(self,num):
    self.result -= num
    return self.result

```

#### 클래스와 객체

ex ) 과자의 틀 - 클래스, 과자틀에 의해 만들어진 과자 - 객체

```python
class Cookie:
    pass

a =Cookie()
b =Cookie()
```

- `Cookie()` 의 결과값을 돌려받은 a,b 를 객체라 부를 수 있음, 함수를 사용해 결과값 돌려받는 모습과 비슷

#### `객체와 인스턴스의 차이`

클래스로 만든 객체 -> 인스턴스, a=Cookie(), a 는 객체 a객체는 Cookie의 인스턴스이다.

인스턴스는 특정 객체가 어떤 클래스의 객체인지 관계위주로 설명할 때 사용함

'a 는 객체', 'a는 Cookie의 인스턴스'

#### 객체에 숫자 지정할 수 있게 만들기

객체 a는 아직 아무런 기능도 하지 못함, 더하기,나누기,곱하기,빼기 등 객체를 만들어야 함,  2개의 숫자를 먼저 알려주어야 함

`a.setdata(4,2)`

```python
class FourCal:
    def setdata(self,first,second): #method의 매개변수
        self.first= first			#method의 수행문
        self.second = second		#method의 수행문
        
a = FourCal
a.setdata(4,2)
```

- setdata 함수를 만들고 클래스 안에 method를 생성

- 첫 번째 매개변수 self에는 setdata method를 호출한 객체 a가 자동으로 전달됨

```python
a = FourCal()
FourCal.setdata(a,4,2)
# 잘 사용하지는 않지만 다음과 같이 클래스를 통해 method 호출 가능

self.first=4
self.second=2

class FourCal():
  num=0;num=0
  def setdata(self,num,num2):
    self.num =num;self.num2=num2

   
  def add(self):
    return self.num+ self.num2
  


a=FourCal()
b=FourCal()
a.setdata(4,2)
b.setdata(5,2)
b.num
```

- a 객체값은 b 객체에 영향 받지 않고 원래 값을 유지하고 있다. 클래스로 만든 객체의 변수는 독립적인 값을 유지한다

```python
class FourCal():
  def setdata(self,num,num2):
    self.num =num;self.num2=num2
  
  def add(self):
    return self.num+ self.num2
  
  def mul(self):
    return self.num*self.num2
  def sub(self):
    return self.num - self.num2
  def div(self):
    return self.num/self.num2

a=FourCal()
a.setdata(4,5)
print(a.add())
print(a.sub())
print(a.mul())
print(a.div())
```

#### 생성자(Constructor)

- FourCal 클래스의 인스턴스 a에 setdata 메서드를 수행하지 않고 add 메서드를 수행하면 "AttributeError: 'FourCal' object has no attribute 'first'" 오류가 발생한다. setdata 메서드를 수행해야 객체 a의 객체변수 num,num2가 생성되기 때문

- 초기 값을 설정할 필요가 있을 때 , 초기값을 설정하기 보다는, 생성자를 구현하는 것이 안전한 방법,
- 생성자 - 객체가 생성될 때 자동으로 호출되는 method를 의미

- method 이름으로 `__init__`을 사용하면 method 생성자가 생성

- method 이름을 `__init__`으로 생성하면 생성자로 인식되어 객체가 생성되는 시점에 자동을 호출되는 차이가 있음
- `setdata`를 굳이 불러올 필요가 없음 
  - **FourCal().setdata(4,5)   ->   FourCal(4,5)**  

#### 클래스의 상속

클래스의 기능을 물려받을 수 있게 만드는 것이다. 

```python
class MoreFourCal(FourCal):
    pass
#class를 상속하기 위해서는 다음처럼 클래스 이름 뒤 괄호 안에 상속할 클래스 이름을 넣어 주면 됨
#상속 받았으므로 모든 능을 사용 할 수 있어야 함
```

- 기존 클래스를 변경하지 않고 기능을 추가하거나 , 기존 기능을 변경하려고 할 때 사용

- 기존 클래스가 라이브러리 형태로 제공 or 수정 허용 x면 상속을 해야 함

#### method 오버라이딩

```python
a = FourCal(4,0)
a.div()
# 0으로 나눌 때 오류가 아닌 0으로 돌려주고 싶을때 덮어씌우기를 한다

class SateFourCal(FourCal):
    def div(self):
        if self.num2 == 0:
            return 0
       	else:
            return self.num/self.num2
#덮어씌운 method가 호출된다

```

#### 클래스 변수

```python
class Family:
    lastname = "김"
    
print(Family.lastname)
```

`Family`에 선언한 `lastname` 이 클래스 변수이다.

```python
a= Family()
b= Family()
print(a.lastname) 김
print(b.lastname) 김
# '박' 으로 변경 될 시 모두 박으로 변경됨
```

class 는 모두 공유된다는 사실을 알 수 있다

- 하지만 class 변수 보다는 객체 변수가 더 중요하다 / 사용 비율이 훨씬 높다!!!