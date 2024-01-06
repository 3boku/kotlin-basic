# Kotlin 기본 문법

## Main함수
```kotlin
fun main() {
    명령어
}
```
이런식으로 메인함수는 생김

## print
```kotlin
fun main() {
    print("hello world!")
    println("hello world")
}
```
자바처럼 그냥 print와 println이 있음 println은 줄바꿈 그리고 세미콜론은 안붙임

##변수

```kotlin
fun main() {
    var i = 10
    var name = "3boku"
    var point = 3.3
    //따로 타입 선언 안해줘도됨

    var i2 : Int = 10
    var name2 : String = "3boku"
    var point2 : Double = 3.3
    //타입 지정해줄때는 콜론 찍고 대문자로 시작하는 타입 적어주기
    //자바에 있는 모든 타입 사용 가능 다만 대문자로 시작
}
```

## 상수
```kotlin
fun main() {
    val primary = 20
    //기본 상수형
}
```