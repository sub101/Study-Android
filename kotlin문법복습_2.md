### 1. 클래스 정의와 인스턴스 생성

클래스 = 변수(필드)와 메소드로 구성
객체지향 관점에서, 클래스를 실세계의 객체들이 가질 수 있는 상태와 행동으로 정의.

ex) class Person{
    ...
}

fun main(){
    var person1 : Person = Person() // 생성자를 이용해 객체 생성
}

### 2. 생성자
##### constructor() 메소드를 사용하고 필요하다면 파라미터 지정 가능.

ex) constructor(job : String, age : Int){
    this.color = color // 지역변수에 전역변수 대입
    this.speen = speed
}

fun main(){
    var person1 : Person = Person("학생", 18)
}

### 3. 메소드 오버로딩

:한 클래스 내에서 메소드의 이름이 같아도 파라미터의 개수나 데이터 형식만 다르면 여러 개를 선언할 수 있음.

단, 매개변수 다르게 함.

ex) class Car {
    var color : String = ""
    var speed : Int = 0

    constructor(color : String, speed : Int){
        this.color = color
        this.speed = speed
    }

    constructor(speed : Int) {
        this.speed = speed
    }

    constructor(){

    }
}

### 4. 정적 필드, 정적 메소드, 상수 필드

정적 필드 : 인스턴스를 생성하지 않고 클래스 자체에서 사용되는 변수가 필요
- companion object{} 안에 필드를 작성
- companion object {} 안에 메소드 작성시 -> 정적 메소드
* 정적 메소드는 인스턴스를 생성하지 않고도 호출 가능 -> 클래스명.메소드명()
- 상수 필드 : const val 선언 (대문자 구성이 일반적)
* 선언 후 값 변경 불가

### 5. 클래스 상속과 메소드 오버라이딩

클래스 상속 : 기존의 클래스가 가지고 있는 것을 그대로 물려받으면서 필요한 필드나 메소드를 추가로 정의하는 것
- open을 써야 상속 받을 수 O 

메소드 오버라이딩 : 부모 {클래스의 메소드를 무시하고 새로 정의

ex) open class Car{ //클래스 상속 허용을 위한 open
    ...
    open fun upSpeed(value : Int){ //메소드 오버라이딩을 허용하기 위한 open
        if(speed+value>=200){
            ...
    }
}

class Automobile : Car {
    var seatNum : Int = 0

    constructor(){

    }

    fun countSeatNum() : Int {
        return seatNum
    }

    override fun upSpeed(value: Int){
        if(speed+value>=300){ //내용 바꿈
            ...
        }
    }
}

ex2) fun main() {
    var auto : Automobile = Automobile()
    // 객체 생성 및 선언 (Automobile() : 생성자)
    //클래스로 인스턴스 생성 (상속 받음)

    auto.upspeed(250)
}

### 6. 추상 클래스와 추상 메소드

추상클래스 = 인스턴스화를 금지하는 클래스 (클래스로 인스턴스 생성하는 것)
- abstract 키워드 붙여서 지정
- 추상메소들르 포함하는 클래스는 추상 클래스로 지정해야
- 추상클래스 & 추상메소드 목적
: 공통적으로 사용되는 기능을 추상 메소드로 선언해놓고, 추상 클래스를 상속받은 후에 반드시 추상 메소드를 오버라이딩해서 사용하기위함.
- 추상메소드를 오버라이딩 하는 것 = 추상메소드를 구현한다

ex) abstract class Animal {
    var name : String = ""
    abstract fun move()
}

class Tiger : Animal(){ //괄호 O
   var age : Int =0 //필드는 조정가능
   override fun move() {
       println("네 발로 이동")
   }
}

class Eagle : Animal(){
    var home : String = ""
    override fun move() {
        println("날개로 날아간다")
    }
}

fun main() {
    var tiger1 = Tiger()
    var Eagle1 = Eagle()

    tiger1.move()
    eagle1.move()
}

### 7. 클래스 변수의 다형성
다형성 : 서브클래스에서 생성한 인스턴스를 자신의 클래스 변수에 대입할 수 있음
다형성을 이용해, 하나의 변수에 여러 종류의 인스턴스를 대입할 수 O

ex) fun main(){
    //Animal : 추상클래스
    //Tiger, Eale : Animal 상속받은 서브클래스

    var animal : Animal
    //데이터 형식만 지정 (값 아직 지정 X)

    animal = Tiger() //<- 값
    animal.move
    // 네 발로 이동한다.

    animal = Eagle() //<- 값
    animal.move()
    //날개로 날아간다.
    //동일한 변수명으로 객체 받아 사용
}

### 8. 인터페이스와 다중 상속
- interface 키워드로 정의
- 내부에는 추상 메소드 선언
- 상속과 마찬가지로 클래스에서 인터페이스를 받아 완성할 때 ': 인터페이스 이름' 형식
- kotlin, 다중 상속 지원하지 않음
- 인터페이스는  '구현한다'고 표현

ex) abstract class Animal {
    var name : String = ""
    abstract fun move()
}

interface iAnimal {
    abstract fun eat()
}

class iCat : iAmimal {
    overrride fun eat() {
        println("생선을 좋아함")
    }
}

class iTiger : Animal(),iAnimal {
    //추상클래스와 인터페이스 (추상클래스는 괄호O , 인터페이스는 괄호X)
    override fun move(){
        println("네 발로 이동")
    }

    override fun eat(){
        println("육식이다")
    }
}

fun main() {
    var cat = iCat()
    cat.eat()

    var tiger = iTiger()
    tiger.move()
    tiger.eat()
}

### 9. 람다식

: 함수를 익명 함수 형태로 간단히 표현
- 람다는 {} 안에 매개변수와 메소드의 모든 내용을 선언

[람다식 특징]
- 람다식은 {}로 감싼다.
- {}안 ->의 왼쪽은 파라미터/ 오른쪽은 함수의 내용
- 내용 중 마지막 문장이 return값
- 오른쪽 문장이 여러개시 ;으로 구분

ex) fun addNum (n1 : Int, n2: Int){
    return n1 + n2
}

// val addNum = {n1: Int,n2:Int -> n1 + n2} 과 동일