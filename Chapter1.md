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
  
### Null-Pointer Exception

이 때 발생하는것이 NPE이다.

코틀린은 NPE를 방지하기 위해 언어 차원의 시스템을 가지고 있다.

물음표 ? 을 data type뒤에 붙이면 **optional**한 data type이 된다. 

optional은 컴파일러에게 **이 object가 null을 담을 수도 있다**고 알려준다.

작은 디테일이 코드에서 연쇄 효과를 만들어낸다.

- Optional을 사용할 때 **safe-call 연산자**를 사용해야 한다.

  ```car?.drive()```
  
  safe-call 연산자는 객체가 **null이 아닐 때에만 함수가 동작한다**는 것을 의미한다.

- null일 수도 있는 변수를 대입할 때 **엘비스 연산자 (?:)** 를 사용한다. 

  ```val immutableCar: Car = car ?: Car("Porche")```
  
  immutableCar은 Optional이 아니기 때문에 null이 아니고 drive할 수 있다고 확신할 수 있다. 
  
  immutableCar는 car이 되거나 Porche가 된다. (car가 null이라면)

변수가 null이 아닌 것을 알 때 (Optional임에도) 그 값을 사용하려 한다면

- not-null assertion operator !! 사용

  ```car!!.drive()```
  
  car가 담고있는 non-null value에 대해 drive()를 호출한다. null인 경우 NPE를 던진다. 사용할 때 Think! Twice!하라고 !!이다...
  
## Conditional statements

코틀린의 프로그램들은 선형적으로 실행된다. (즉, 한 번에 한 줄씩 실행된다.)

결정을 내리거나 (decision making) 반복을 해야 (repeating a step) 할 필요가 있다.

### decision making

- if-else
- when
  여러 케이스를 다룰 수 있는 연속된 if-else

- else는 optional

## Loops

- for
- while

### for

어떠한 iterable collection에 대해 iterate할 수 있다.
```
for (i in 1..3) { // 1..3 : IntRange
  println(i)
}
```

```for (item in collection) println(item) // collection 안의 모든 아이템들을 출력 ``` 

### while

condition이 true로 유지되는 한 같은 블록을 계속해서 실행한다.

```
var x = 10
while (x > 0) { // x == 0 이 되어 condition이 false가 되면 종료
  x--
}
```

do-while loop는 한 번 실행 후 condition이 true일 때 반복 실행
```
var x = 10
do {
  x--
} while (x > 0)
```

infinite loop 생성 -> StackOverflowException 발생
```
var x = 10
while (x > 10) { //무한히 true
  x++
}
println("출력되지 못함")
```

