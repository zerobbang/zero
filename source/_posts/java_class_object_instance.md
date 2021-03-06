---
title: JAVA - 객체와 클래스, 인스턴스
date : "2022-06-23"
categories:
- [Java]
tag:
- [Object]
- [Class]
- [Instance]
---

♦ **중요** - 객체 vs 클래스 vs 인스턴스

> 객체 : 구현할 **실제 대상**
클래스 : 객체 만들기 위한 **설계도**
인스터스 : 설계도를 통해 **구현**한 실체
> 

### 객체 Object

우리가 **설계도**를 통해 **구현**할 실제 대상 → **클래스**의 **인스턴스**

- 클래스 ( 설계도 )에서 선언한 그대로 생설될 실제 대상
- 객체 지향 프로그래밍 관점에서 보면 클래스의 타입으로 선언 → **객체**
    
    ```java
    // Peplel 이라는 class
    public class People { ... }
    
    // 객체 ( Main 클래스 에서 )
    People me;
    People you;
    // -> People이라는 클래스 (설계도)를 통해서 me와 you 라는 객체를 생성.
    
    // 동시 생성 가능
    // People me, you;
    ```
    
- 모든 인스턴스( 구현 )을 대표하기도 한다.

### 클래스 Class

객체를 생성하기 위한 **설계도**

객체의 속성(변수)과 행동(메서드)의 집합

### 인스턴스 Instance

클래스( 설계도 )를 바탕으로 **구현한 설계**

객체 ( 구현 대상 )을 실체화 한 것을 의미

```java
// 위에 이어서

// 객체의 인스턴스화
// 객체를 메모리에 할당
me = new People();
you = new People();

// new Class명(); -> 인스턴스 생성
```

- 객체는 클래스의 인스턴스
- 실행 프로세스는 프로그램의 인스턴스(실체화 / 구현)이다
- 인스턴스는 한 추상적 개념으로부터 생성된 복제본

- new
    
    다음으로 나오는 생성자( People() )를 인스턴스로 생성하고 Heap 영역 메모리에 할당한다.
    
    `Class Type 변수명 = new People();`
    
    ```java
    // ClassType 변수명 = new 생성자();
    People me = new People();
    
    // People이라는 클래스 타입으로 me라는 변수명에 객체를 생성한다.
    // Class명();을 통해 해당 class의 생성자를 호출하고,
    // new를 통해 호출된 생성자를 인스턴스화(메모리에 할당) 하고 
    // new로 통해 최종 생성된 인스턴스를 아까 me라는 변수에 저장.
    ```
    

---

## 정리

- 클래스 타입으로 선언 하면 객체가 생성이 된다.
- 객체가 메모리에 할당되어서 실제 사용되면 인스턴스라고 한다.
- 객체를 클래스의 인스턴스화를 통해 실체화하면 메모리에 할당이 된다.

---

[[참고 블로그]](https://gmlwjd9405.github.io/2018/09/17/class-object-instance.html)

**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**