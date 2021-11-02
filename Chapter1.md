# Chapter 1 : Kotlin & Kotlin Standard Library

## 1. Introduction to Kotlin
자료구조와 알고리즘을 이해하기 위해 언어의 main features를 이해해야 한다. 
자료구조를 깊게 배우기 위해 알아야 하는 것들
- How to declare **variables** and **functions**
- How to create **custom data types**
- How to manipulate data in **loops** and **decision-making structures**

이후에는 더욱 복잡한 **Generic**을 배우게 된다.

## 2. Variables and data types
variable은 정보를 저장하는 방식, 이름과 data type을 가진다. modifier 또한 가질 수 있다.

### val 과 var
val로 선언된 변수는 재할당될 수 없다. (컴파일 에러 발생) 

### type inference
코틀린 컴파일러가 variable의 data type을 결정한다. 이러한 기능은 대부분의 모던 프로그래밍 언어가 가지고 있다. 

**변수가 선언될 때 초기화 된다면** 컴파일러는 타입을 확실히 알 수 있다. 이럴 때 data type을 명시할 필요가 없다. 

선언만 하고 나중에 초기화할 수도 있다. 이럴 때에는 data type을 명시해야 한다.

### basic data types in Kotlin

- Numbers : Double, Float, Long, Int, Short, Byte
- Characters : Char, String
- Other : Boolean, Array

## 3. Optionals and null-safety

많은 프로그래밍 언어는 null value의 개념을 가지고 있다.

**객체가 어떤 값도 가지고 있지 않다** 라는 의미를 표현할 때 변수에 null을 대입한다.

- Car를 가질 수 있는 변수가 있지만 아직 Car 객체를 생성하지 않았을 때

  ``` var car: Car? = null ```
- 객체를 생성한 뒤에

  ``` car = Car("Mercedes-Benz")```
  
- null의 문제점은 이를 사용하려고 할 수 있다는 것이다.

  ``` car.drive() ```
  
**→→ Null-Pointer Exception**
