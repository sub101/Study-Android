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

### 5. 클래스 상속과 메소드 오버라이딩

### 6. 추상 클래스와 추상 메소드

### 7. 클래스 변수의 다형성

### 8. 인터페이스와 다중 상속

### 9. 람다식