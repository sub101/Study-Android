### 1. 변수와 데이터 형식
var (변수명) : (데이터 형식)  
ex) var i : Int = 10

#### 문자형
char  
String

#### 정수형
Byte  
Short  
Int  
Long  

#### 실수형
Float  
Double  

#### 불리언형
Boolean 

- kotlin은 변수를 선언할 때 암시적인 방법도 제공
- 암시적 선언은 변수의 데이터 형식을 지정하지 않고, 대입되는 값에 따라 자동으로 변수의 데이터 형식이 지정되는 것.
- 초기화하지 않는 경우에는 데이터 형식을 반드시 명시해야한다.

#### var (variable) : 변수
일반 변수를 선언할 때 사용
필요할 때마다 계속 다른 값을 대입 가능

#### val (value) : 상수
변수 선언과 동시에 값 대입 or 초기화 없이 선언한 후에 한 번만 대입

#### 데이터 형식 변환
##### 1. 캐스팅 연산자

##### 2. 정적 메소드
toInt() / toDouble ...  
ex) var a : Int = "100".toInt()  
// String -> Integer  

var b : Double = "100.123".toDouble()  
// String -> Double  

- kotlin, 기본적으로 변수에 null값을 넣지 못함.  
: null 값을 대입하려면 변수를 선언할 때 데이터 형식 뒤에  ? 를 붙임.  

ex) var a : Int? = null  

- 변수 객체가 null값이 아니라고 표시해야 할 경우  
: !!  

ex) var ary = ArrayList<Int>(1) //1개짜리 배열 리스트  
ary!!.add(100) // 값 100을 추가  
//ary에 null값이 들어가면 안됨.  

### 2. 조건문 : if, when  
#### if문  
if(조건식){  
    //조건식 true일 때 이 부분 실행
}else{
    //조건식 false일 때 이 부분 실행
}

#### when 문 : java의 switch ~ case
when(식){
    값1 -> // 식 = 값1, 이 부분 실행
    값2,값3,값4 -> // 식 = [값2,값3,값4],  이 부분 실행
    .
    .
    .
    else -> //어디에도 해당하지 않으면 이 부분 실행
}

- when은 무조건 마지막 else로 끝남.

##### when문 처리 방법
- 범위 처리 
1. in a..b  
: a <= x <= b  

2. a until b  
: a <= x < b  


### 3. 배열
: 여러 개의 데이터를 하나의 변수에 저장하기 위해 사용  

- 일차원 배열 선언  
var 배열명 = Array<데이터 형식>(개수, {초깃값})
var 배열병 = Array<데이터 형식>(개수){초깃값}

ex) var ary = Array<Int>{4,{0}} 
//4개 모두 0으로 채움
ary[0] = 10

- 이차원 배열 선언
var 배열명 = Array<배열 데이터 형식>(행 개수,{배열 데이터 형식(열 개수)}) 
//초깃값 없음

ex) var arytwo = Array<IntArray>(3,{IntArray(4)}) //초깃값 지정 안 함
arytwo[0][0] = 100

ex2) var ary : IntArray = intArrayOf(1,2,3)
//크기가 3인 배열에 1,2,3을 넣음

- ArrayList 사용해 배열 쉽게 다루기
var one = ArrayList<Int>(4)
one.add(10) // one[0]
one.add(20) // one[1]
var hap = one.get(0) + one.get(1) //30

### 4. 반복문 : for, while

##### for

- <가장 많이 사용되는 for문 형식>

for(변수 in 시작..끝 step 증가량){
    //이 부분 반복
}

- <배열의 개수만큼 변수에 대입하여 반복하는 방법>

for(변수 in 배열명.indices){
    //indices : index의 복수형
    //이 부분 반복
}

ex) var one : IntArray = intArrayOf(10,20,30,40)
    var two : Array<String> = arrayOf("a","b","c")

    for(i in one.indices){
        println(one[i])
    }

- <배열 사용시 i없이 바로 배열의 값을 하나씩 처리>
for(변수 in 배열명){
    //이 부분에서 변수 사용
}    

##### while
while(조건식){
    //true인 동안 반복실행
}


### 5.메소드와 전역변수, 지역변수

##### 메소드
기본 메소드인 main()함수 외에 사용자가 메소드를 추가로 생성 가능.

ex) fun add(num1 : Int, num2 : Int) : Int {
    var hap : Int
    hap = num1 + num2
    return hap
}

##### 전역변수 & 지역변수
전역변수, 모든 메소드에서 사용됨. // main 함수 밖에 선언
지역변수, 메소드 내부에서만 사용됨.
전역변수와 지역변수 이름 같아도 됨 -> 보통 지역변수 참조



### 6. 예외 처리 : try ~ catch
ex) fun main(){
    var num1 : Int = 100
    var num2 : Int = 0

    try{
        println(num1/num2)
    }catch(e : ArithmeticException){
        println("계산에 문제가 있습니다")
    }    
}