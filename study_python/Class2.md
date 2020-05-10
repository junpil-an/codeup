## Class

#### 특징

- 클래스는 객체(인스턴스)를 생성하기 위해 필요
- 객체지향 프로그래밍(OOP)를 위해 사용됨
- OOP의 특징 - 추상화,캡슐화(정보은닉),상속,다형성
- 프로그램 유지보수를 편리하게 만듦
- 파이썬의 모든 데이터, 함수는 객체
- 클래스에는 속성(멤버 변수) , 메소드(멤버 함수),생성자,소멸자

```python
class robot:
    name= 'robot'
    def info(self):
        print("나의 이름은", self.name,"이다")
        
robot().info()
# 나의 이름은 robot이다
robot().name
#'robot'
isinstance(robot(),int)
# false
isinstance(robot(),robot)
# True
```

- 클래스 내에 속성(변수)과 메소드(함수) 포함
- 메소드의 첫 번째 인자로 self를 전달
- self는 하나의 클래스에서 만들어진 여러 객체(instance)를 구별하기 위해 사용됨
- isinstance()를 사용하여 어느 클래스의 객체(인스턴스)인지 확인함

#### 생성자,소멸자

```python
class robot:
    name='robot'
    age=0
    def __init__(self,name,age):
        print("생성자호출")
        self.name=name
        self.age=age
    def __del__(self):
        print('소멸자 호출')
    def info(self):
        print('나의 이름은',self.name,'이다')
        print('나의 나이는',self.age,'이다')
r= robot('bill',7)
#"생성자호출"
r.info()
#나의 이름은 bill이다
#나의 나이는 7이다
del r
#소멸자 호출
```

- 객체가 만들어질 때 호출되는 함수를 생성자`(__init__)`
- 생성자 객체를 초기화 할 때 자주 사용됨
- 객체가 사라질 때 호출되는 함수를 소멸자 `(__del__)`

#### Class 상속

```python
class robot:
    name = 'robot'
    age = 0
    def __init__(self,name,age):
        print('robot 생성자 호출')
        self.name = name
        self.age= age
    def__del__(self):
        print('robot 소멸자 호출')
        
    def info(self):
        print('나의 이름은',self.name,'이다')
        print('나의 나이는',self.age,'이다')
        
class strong_robot(robot):
    weapon = 'gun'
    def __init__(self,name,age,weapon):
        print('strong_robot 생성자 호출')
        super().__init__(name,age)
        self.weapon=weapon
        
    def info(self): #오버라이딩?
    	super().info()
        print(self.weapon,'로 싸운다')
        
s= strong_robot('hulk',3,'sorwd')
#strong_robot 생성자 호출
#robot 생성자 호출
s.info()
#나의 이름은 hulk이다
#나의 나이는 3이다
#sowrd로 싸운다
```

- 상속 받고 싶은 부모 클래스를 괄호 안에 입력
- 상속을 받으면 부모 클래스의 모든 내용이 자식에게 전달
- 부모 클래스를 메소드로 사용하기 위해 super() 함수를 사용
- 부모 class가 제공하는 method를 자식이 재정의 할 수 있음
- python은 다중 상속을 지원

#### 파이썬 get,set method 함수 사용

```python
class test:
    data=10
    
t= test()
#10
```

- python 은 기본적으로 직접 속성에 접근할 수 있음   (**편하지만 위험**)

```python
class test:
    __data=10
    def getData(self):
        return self.__data
    def setData(self,data):
        self.__data=data
t= test()
t.getData()
#10
t.setData(20)
#20
```

- **속정 이름 앞에 언더바 2개를 쓰면 외부에서 속성에 접근할 수 없음**

- get,set method를 사용하여 속성을 다룬다

#### python Class method vs instance method

```python
class test:
    data = 10 #class 속성
    def __init__(self,data):
        self.data = data #instance
    
    def printClass(cls): #클래스 메소드
        print(cls.data)
    
    def printInstance(self): #인스턴스 메소드
        print(self.data)
```

- method는 기본적으로 self를 전달하는 instance method
- class method는 class 이름으로 호출 할 수 있다 ex) text.printClass()
- 클래스 속성, 클래스 메소드는 모든 객체가 공유한다

```python
class hello(object):
  def __init__(self,name,age):
    self.name=name
    self.age=age
    print("설정완료")
  def __del__(self):
    print("삭제되었다")

  def call(self):
    print("난",self.name,self.age,"이다")


#h=hello('안준필',30)
class hello_hello(hello):
  bobby= 'tennis'
  def __init__(self,name,age,hobby):
    print("hello 생성자 호출")
    super().__init__(name,age)
    self.hobby = hobby
  
  def info(self):
    super().call()
    print(self.hobby,'를 잘한다')

a= hello_hello('준필',30,'tt')

a.info()
```

