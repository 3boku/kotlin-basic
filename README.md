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

## 변수

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
const val num = 10 //탑레벨 상수는 이렇게 메인함수 위에 const를 붙여서 선언

fun main() {
    val primary = 20
    //기본 상수형
}
```

## 형변환
```kotlin
fun main() {
    var i = 10
    var l = 20L // L은 long임

    l = i.toLong()
    i = l.toInt()
    //l은 long타입이고, i는 int타입이라 대입을 해주기 위해선 형변환을 해줘야함

    var name = "10"

    name = i.toString()
    i = name.toInt()
    //name은 string타입이고, i는 int타입이니까 형변환을 해서 대입을 해준다
    //형변환 명령어는 변수명.toString(), 변수명.toDouble() 등등
}
```

## String
```kotlin
fun main() {
    var name = "hello"
    println(name.uppercase()) //자바처럼 toUppercase()가 아님
    println(name.lowercase())
    println(name[0]) // 배열처럼 문자만 출력 가능
    println("제이름은 " + name + "입니다") //자바처럼 변수랑 텍스트 섞어서 쓸수있지만
    println("제이름은 $name 입니다.") //이렇게도 사용함 얘는 뒤를 스페이스를 넣어줘야함
    println("제이름은 {$name + 10}입니다.") //수식을 넣거나 스페이스를 넣지 말아야하는 상황엔 중괄홀로 감싸줌
}
```

## max, min
```kotlin
fun main() {
    var i = 10
    var j = 20

    println(kotlin.math.max(i, j))
    println(kotlin.math.min(i, j))
    //코틀린안에 math패키지안에 있는 max와 min
}
```

## random
```kotlin
import kotlin.random.Random

fun main() {
    val randomNumber = Random.nextInt(0, 100)
    // Random패키지안에 nextDouble, nextInt등을 사용해서 난수를 만들 수 있음, 보이는 것처럼 범위를 지정해줄 수 있고, 앞은 포함 뒤는 포함 안됨.
    print(randomNumber)
}
```

## 키보드 입력
```kotlin
import java.util.Scanner

fun main() {
    val reader = Scanner(System.`in`)
    reader.nextInt()
    reader.next()
    //자바에서 사용하는 Scanner를 사용, 코틀린에 없는 명령어는 ` `으로 감싸서 사용
}
```

## 조건문
```kotlin
fun main() {
    var i = 5
    if (i > 10){
        print("10 보다 크다")
    } else if (i > 5){
        print("5 보다 크다")
    } else {
        print("작다")
    }
    //if문은 자바와 똑같음

    when {
        i > 10 -> {
            print("10보다 크다.")
        }
        i > 5 -> {
            print("5보다 크다")
        }
        else -> {
            print("작다")
        }
    }
    //자바의 Select와 비슷하지만 훨씬 좋음

    var result = if (i > 10){
        "10 보다 크다"
    } else if (i > 5){
        "5 보다 크다"
    } else {
        "작다"
    }

    var result2 = when {
        i > 10 -> {
            "10보다 크다."
        }
        i > 5 -> {
            "5보다 크다"
        }
        else -> {
            "작다"
        }
    }
    print(result)
    print(result2)
    //kotlin에서의 조건문은 식으로 치환되기때문에 값을 리턴할 수 있음
    //그래서 삼항 연산자가 없고 if문을 사요함
}
```

## 반복문
```kotlin
fun main() {
    val items = listOf(1,2,3,4,5)

    for (item in items) {
        print(item)
    }
    //자바처럼 이렇게 쓸 수도 있지만

    items.forEach { item -> print(item)}
    // forEach 함수를 사용해서 리스트 값들을 받아올 수 있음

    for(i in 0..3) {
        print(i)
    }
    //이건 for(int i = 0 ; i <= 3 ; i++)와 같은코드

    for ( i in 0..(items.size - 1)) {
        print(items[i])
    }
    //lengh를 안쓰고 size를 씀
    
    //while은 자바와 완전 같음, break, continue도 다 있음
}
```

## List
```kotlin
fun main() {
    var items1 = listOf(1,2,3,4,5)
    //리스트 내용이 변경이 안됨
    
    var items2 = mutableListOf(1, 2, 3, 4, 5)
    //리스트 내용이 변경 가능한 리스트
    
    items2.add(6)
    items2.remove(3)
    //이렇게 수정 가능
}
```

## 배열
```kotlin
fun main() {
    val items = arrayOf(1, 2, 3) //배열을 만들때는 arrayOf명령어를 씀
    items[0] = 1
    items.get(2)
    //이렇게 불러올 수 있음
    
    try {
        val item = items[4]
    } catch (e: Exception) {
        print(e.message)
    }
    //try catch문도 똑같음
}
```

## Null Safety
```kotlin
fun main() {
    val name = null
    //만약에 변수가 null값이 들어있으면 타입을 지정해 줘야함 그래서 저건 틀렸음

    var name1: String? = null
    //타입 지정해주고, 타입뒤에 ?를 적어줘야함

    name1 = "현서"
    //?를 쓰면 null이였다가 값을 대입할 수 있음

    name1?.let {
        name1 = name
    }
    //이런식으로 쓰면 Null Check가 가능하고, 다시 Null값으로 대입이 가능함
}
```

## 함수
```kotlin
fun main() {
    print(sum(a=10,b=20))
    print(sum(b=10,a=20))
    //이렇게 매개변수의 순서를 바꿔서 대입도 가능
}

fun sum(a: Int, b: Int) : Int{
    return a + b
}
//안에 매개변수를 넣어주고, 매개변수의 인풋타입을 가져야함, 그리고 반환할 타입을 지정함

fun sum1(a: Int, b: Int) = a + b
//이렇게 사용도 가능 같은코드임
```

## Class
```kotlin
fun main() {
    val john = Person("John", 20)
    print(john.age)

    john.age = 23
}
//이렇게 파라미터에 접근할 수 있음

class Person(
    private val name: String, // private도 사용가능 기본은 퍼블
    var age: Int
)
//클래스를 만들땐 따로 라인에 들어가서 만들지 않고, 한 줄에 모두 쓸 수 있음
```

## getter, setter
```kotlin
fun main() {
    val john = Person("John", 20)
    val john2 = Person("John", 20)

    print(john == john2)
    //아무것도 안하면 false가 나옴 다른 객체임
    john.hobby = "야구"
}

data class Person(
    val name: String,
    var age: Int
) {
    var hobby = "축구"
    //class내부에서 만든 변수는 메인에서 쓸 수 있다.

    init {
        print("init")
    } //이렇게 생성자가 만들어줬다고 할 수도 있다
}
//앞에 data만 붙이면 같은 값을 갖고있으면 모두 같은 객체로 분류함
```

## 상속
```kotlin
fun main() {

}


class Dog1 {
    fun move() {
        //
    }
}

class Cat1 {
    fun move() {
        //
    }
}
// 이런식으로 클래스에 같은 함수가 있으면

abstract class Animal {
    open fun move(){
        print("이동")
    }
    //상속받아도 오버라이드가 자동으로 안되서 open을 사용해야함
}

class Dog : Animal() {
    override fun move() {
        println("껑충")
    }
}

class Cat : Animal() {
    override fun move() {
        println("살금")
    }
    //이런식으로 오버라이드 가능
}
// 이런식으로 상속할 수 있음

class Humon()
//이렇게 일반 클래스를 만들면

class cath : Humon()
//이런식으로 상속이 안됨


open class Humonn2()

class gc : Humonn2()
//얘도 앞에 open을 쳐줘야 상속가능
```

## Interface
```kotlin
fun main() {

}

interface Drawble {
    fun draw()
}
//이렇게 인터페이스를 만들면

abstract class Animal {
    open fun move(){
        print("이동")
    }
}

class Dog : Animal(), Drawble { // 소괄호 안치고 사용 가능
    override fun move() {
        println("껑충")
    }
    
    override fun draw() {
        print("Draw")
    }
}

class Cat : Animal() {
    override fun move() {
        println("살금")
    }
    //이런식으로 오버라이드 가능
}
```

## 타입체크
```kotlin
fun main() {
    val dog = Dog()
    val cat = Cat()

    if (dog is Dog) {
        println("개")
    }
    //이렇게 타입체크를 할땐 is를 사용함
}

interface Drawble {
    fun draw()
}
//이렇게 인터페이스를 만들면

abstract class Animal {
    open fun move(){
        print("이동")
    }
}

class Dog : Animal(), Drawble { // 소괄호 안치고 사용 가능
    override fun move() {
        println("껑충")
    }

    override fun draw() {
        print("Draw")
    }
}

class Cat : Animal() {
    override fun move() {
        println("살금")
    }
    //이런식으로 오버라이드 가능
}
```

## 강제 형변환 as
```kotlin
fun main() {
    val box = Box(10)
    val box2 = Box("dfdf")

    print(box.value)
}

class BoxT<T>(value:T) {

}
//여기 안써져있는데 위에 is처럼 as쓰면 됨
```