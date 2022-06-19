---
title: JAVA - 얕은 복사와 깊은 복사
date : "2022-06-15"
categories:
- [Java]
tags:
- [Java]
---

**얕은 복사** : 주소 값만 복사

**깊은 복사**  : 실제 데이터 값을 새로운 메모리에 복사

Main class 와 별도의 다른 copy class 을 만들어 다음과 같이 함수를 만든다.

```java
public class copy {
	String name;
	int age;
	
	// 이름 리턴하는 함수
	public String getName(){
		return name;
	}
	
	// 이름 변경하는 함수
	public void setName(String name){
		this.name = name;
	}

}
```

### 얕은 복사 Shallow Copy

Main Class 파일에서 다음과 같이 복사 한 후 결과를 확인 해 보자.

```java
// copy 객체 인스턴스화
copy orginal = new copy();
// Shallow Copy
copy copy = original;

copy.setName("gayeong");

System.out.println("Shallow Copy");
System.out.println("Original value : "+original.getName());
System.out.println("Copy value : "+copy.getName());
```

![](/images/shallow_deep_copy/Untitled.png)

인스턴스 copy에서만 이름을 변경.

얕은 복사는 주소 값만 복사하여 저장하기 때문에 copy의 이름만 변경했어도 같은 메모리 주소를 갖고 있는 Original에도 동일하게 변경된다.

### 깊은 복사 Deep Copy

깊은 복사를 하는 방법에는 여러가지가 존재한다.

대표적으로는 Cloneable 인터페이스를 사용하는 방법과 복사 생성자, 복사 팩터리 등이 있는데 우선, Cloneable 를 이용해서 해보자

Cloneable 인터페이스를 확장하려면 다음과 같이 추가 코딩이 필요하다.

```java
public class copy implements Cloneable{
	```
	생략 (위 copy class와 동일 )
	```

	@Override
	protected copy clone() throws CloneNotSupportedException{
		return (copy) super.clone();
	}

}
```

Cloneable 인터페이스를 확장 한 후,  clone()을 오버라이드로 리턴 값으로 반환 해야한다.

그리고 Main Class에서도 다음과 같이 변경해주어야 한다.

`public static void main(String[] args) throws CloneNotSupportedException { ``` }`

위 처럼 CloneNotSupportedException을 던져주지 않으면 `Unhandled exception type CloneNotSupportedException error를` 반환한다.

```java
// In Main class
copy original = new copy();
// Deep Copy
copy copyDeep = original.clone();
		
copyDeep.setName("Tina");
System.out.println("Deep Copy");
System.out.println("Original value : "+original.getName());
System.out.println("Copy value : "+copyDeep.getName());
```

![](/images/shallow_deep_copy/Untitled%201.png)

Cloneable 인터페이스를 사용하려면 다음과 같이 사용하면 된다.

그리고 또 다른 방법으로는 try ~ catch 문을 통해서 CloneNotSupportedException을 cathca로 예외처리 하는 방법이 있다.

하지만 Cloneable는 지양하는 것이 좋다.

**Cloneable**

- 복제 가능 여부를 나타내는 class이다. (믹스인 인터페이스)
- Cloneable 구현하지 않은 인스턴스에서 clone을 호출하면 CloneNotSupportedException을 던진다.
- Cloneable 인터페이스는 clone() 메서드의 동작방식 정한다.

**Cloneable 문제점**

- 상위Object 클래스에 protected 접근자로 된 clone() 메서드가 존재하는데 이를 오버라이드 해줘야 한다.
- 생성자를 호출하지 않고 객체를 생성할 수 있게 되어버린다.

### 복사 생성자와 복사 팩토리

```java
// 복사 생성자
public copy (copy original){
	this.name = original.name;
	this.age = original.age;
}

// 복사 팩토리
public static copy copyFun(copy original) {
		copy copy = new copy();
		copy.name = original.name;
		copy.age = original.age;
		return copy;
	}

// in Main Class
copy copyConstructor = new copy(original);
copy copyFactory = copy.copyFun(original);

copyConstructor.setName("Amy");
copyFactory.setName("Diane");
		
System.out.println(original.getName());
System.out.println(copyConstructor.getName());
System.out.println(copyFactory.getName());
```

![](/images/shallow_deep_copy/Untitled%202.png)

---

### 정리

- 인터페이스 만들 때는 절대 Cloneablel 확장해서는 안된다. (지양)
- final Class라면 Clonable을 구현해도 위험은 크지 않지만,  성능 최적화 관점으로 보면 검토한 후에 드물게 허용해야 한다.

---

[[참고 블로그 1]](https://jake-seo-dev.tistory.com/31)

[[참고 블로그 2]](https://zzang9ha.tistory.com/372)

**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**