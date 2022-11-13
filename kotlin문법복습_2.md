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

ex2) 

### 6. 추상 클래스와 추상 메소드

### 7. 클래스 변수의 다형성

### 8. 인터페이스와 다중 상속

### 9. 람다식