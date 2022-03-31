---
title: Python 기초 - Class 생성
date : "2022-03-22"
categories:
- [Python]
---

- class 예

```python
class Person:
  # class attribute
  country = 'korean'

  # instance attribute
  # def __init__(self, ____ ) 고정 표기 변수 담기 위해
  def __init__(self,name,age):
    self.name = name
    self.age = age

  def singing(self, songTitle,sales):
    return "{} {}을 노래합니다. 판매량 {}".format(self.name, songTitle, sales)

if __name__=="__main__":
  kim = Person('Kim',100)
  lee = Person('lee',100)
```

- Class attribute 불러오기

```python
# access class attribute
  print("kim은 {}".format(kim.__class__.country))
  print("lee {}".format(lee.__class__.country
```

클래스 명 첫 글자는 대문자 약속

class attribute 불러올 때는 __class__ 가 약속

- Instance method  불러오기

```python
# call instance method
  print(kim.singing("A",10))
  print(lee.singing("B",20))
```

---

## Class 상속

- 기본 틀 예시

```python
class Parent:
	~

class Child(Parent):
	~

if __name__=="__main__":
	~
```

- 예시

```python
class Parent:
  # instance attribute
  def __init__(self,name,age):
    self.name=name
    self.age=age

  # Instance mathod 정의
  def whoAmI(self):
    print("I'm Parent!!")
  
  def singing(self,Title):
    return "{} {} 노래".format(self.name, Title)

  def dancing(self):
    return "{} 현재 춤을 춘다.".format(self.name)

class Child(Parent):
  def __init__(self,name,age):
    # 부모에서 그대로 가져오기
    super().__init__(name,age)
    print("Child Class is ON")

  def whoAmI(self):
    print("I'm children.")

  def studying(self):
    print("I'm fast runner.")

if __name__=="__main__":
  child_kim = Child("kim",15)
  parent_kim = Parent("kim",45)
  print(child_kim.dancing())
  print(child_kim.singing("연애"))
  # print(parent_kim.studying())  ---> Error  ['Parent' object has no attribute 'studying']
  child_kim.whoAmI()
  parent_kim.whoAmI()
```

- 결과
    
    <aside>
    🍒 Child Class is ON
    kim 현재 춤을 춘다.
    kim 연애 노래
    I'm children.
    I'm Parent!!
    
    </aside>


### Class update

- 속성 값 업데이트

```python
class TV:
  def __init__(self):
    # self.maxprice도 가능
    self.__maxprice = 500

  def sell(self):
    print("Selling Price: {}".format(self.__maxprice))

  # set Mathod, get Mathod
  def setMaxPrice(self, price):
    self.__maxprice = price

if __name__=="__main__":
  tv = TV()
  tv.sell()

# setMaxPrice
tv.setMaxPrice(1000)
tv.sell()
```

- 다음 방식으로는 값이 변하지 않는다.

```python
# change price
# 다음 방식으로는 안바뀜
tv.maxprice = 1000
tv.sell()
```

---

### Class 내부 조건문

```python
class Employee:

  '''
  # init constructor
  def __init__(self,name,salary):
    self.name = name
    self.salary = salary
  '''

  # 다른 버전
  def __init__(self,name,salary=0):  # 1* 
    self.name = name

    if salary >= 0:
      self.salary = salary
    else:
      self.salary = 0
      print("다시 입력해주세요.")

  def update_salary(self,amount):
    # self.salary = self.salary + amount 지양
    self.salary += amount

  def weekly_salary(self):
    return self.salary / 7 

if __name__ == "__main__":
  emp01 = Employee("Tina", - 5000)
  print(emp01.name)
  print(emp01.salary)
  # 1*
  emp01.salary = emp01.salary + 1500
  print(emp01.salary)
  # 2
  emp01.update_salary(3000)
  print(emp01.salary)

  weekly_salary = emp01.weekly_salary()
  print(weekly_salary)
```

- 1*
    
    Class TV 와 달리 private 값이 아니라 외부에서 값을 받아들어온다.
    
    ```python
    # TV
    class TV:
      def __init__(self):         # Private Value
        self.maxprice = 500
        
    # Employee
    class Employee:
      def __init__(self,name,salary=0):  # 외부로부터 값을 받아들임.
        self.name = name
    ```
    
- 결과
    
    <aside>
    🍒 다시 입력해주세요.
    Tina
    0
    1500
    4500
    642.8571428571429
    
    </aside>
    

### Class Docstring

```python
class Person:
  """
  사람을 표현하는 클래스

  '''
  Attributes
  ___________
  name : str
    name of the person

  age : int
    age of the person

  Methods
  ___________

  info(additional=""):
    prints the person a name and age

  """

  def __init__(self, name, age):
    """
    Constructs all the neccessary attributes for the person object
    
    Parameters 매개변수
    ___________________
      name : str
        name of the person

      age : int
        age of the person
    """
    self.name = name
    self.age = age

  def info(self, additional=None):
    """
    Use this if you need additional content.
    
    Parameters 매개변수
    ___________________
      additional : str, optional
        more info to be displayed (Default is None) / A, B, C (에 따라 조건문 실행)
    
    Returns
    ________
      None

    """

    print(f'My name is {self.name}. I am {self.age} years old.' + additional)
  
if __name__=="__main__":
	print(Person.__doc__)
  person = Person("Tina", age = 20)
  print(person.name)
  print(person.age)
  person.info(" 만나서 반가워")
  help(person)
```

- print(person.__doc__)
    
    <aside>
    🍒 사람을 표현하는 클래스
    
      '''
      Attributes
      ___________
      name : str
        name of the person
    
      age : int
        age of the person
    
      Methods
      ___________
    
      info(additional=""):
        prints the person a name and age
    
    </aside>
    
- print(person.name) & print(person.age)
    
    <aside>
    🍒 Tina
    20
    
    </aside>
    
- person.info( “만나서 반가워”)
    
    <aside>
    🍒 My name is Tina. I am 20 years old. 만나서 반가워
    
    </aside>
    
- help(person)
    
    <aside>
    🍒 Help on Person in module **main** object:
    
    </aside>
    
    <aside>
    🍒 class Person(builtins.object)
    |  Person(name, age)
    |
    |  사람을 표현하는 클래스
    |
    |  '''
    |  **Attributes**
    |  ___________
    |  name : str
    |    name of the person
    |
    |  age : int
    |    age of the person
    |
    |  **Methods**
    |  ___________
    |
    |  info(additional=""):
    |    prints the person a name and age
    |
    |  **Methods defined here:**
    |
    |  **init**(self, name, age)
    |      Constructs all the necessary attributes for the person object
    |
    |      Parameters 매개변수
    |      ___________________
    |        name : str
    |          name of the person
    |
    |        age : int
    |          age of the person
    |
    |  **info**(self, additional=None)
    |      Use this if you need additional content.
    |
    |      Parameters 매개변수
    |      ___________________
    |        additional : str, optional
    |          more info to be displayed (Default is None) / A, B, C (에 따라 조건문 실행)
    |
    |
    |      Returns
    |      ________
    |        None
    |
    |  ----------------------------------------------------------------------
    |  Data descriptors defined here:
    |
    |  **dict**
    |      dictionary for instance variables (if defined)
    |
    |  **weakref**
    |      list of weak references to the object (if defined)
    
    </aside>
  
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**