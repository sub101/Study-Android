### 1. 패키지

: 클래스와 인터페이스가 많아지면 관리하기가 어렵기 때문에 패키지 단위로 묶어서 관리

- 사용자가 생성한 클래스가 포함될 패키지는 *.kt 파일 첫행에 
  'package 패키지명' 으로 지정

### 2. 제네릭스

: 데이터 형식의 안전성을 보장하는 데 사용

- 제네릭스를 사용해 strList에 문자열만 들어가도록 설정 가능
- 코드의 마지막 행은 컴파일 오류가 발생하기 때문에 미리 문제점을 확인 가능

ex) var strList = ArrayList<String>(4)
//<String> 없으면 기본형 들어갈 수 O
strList.add("일")  
strList.add("이")  
strList.add(3) //int형이므로 컴파일 오류  

- 제네릭스는 <String>,<Int>,<Double> 등을 사용할 수 있고 사용자가 정의한 클래스형에도 사용 가능

### 3. 문자열 비교, 날짜 형식
##### 문자열 비교
: 문자열을 비교하려면 String클래스의 equals() 메소드를 사용하는 것이 좋다.

ex) var str : String = "hi"  
if(str.equals("hi")){  
  //문자열이 같으면 실행  
}  

##### 날짜 형식
- DateFormat 클래스 사용
- 이를 상속받은 SimpleDateFormat 사용시, '연월일','시분초' 표현 가능

ex>
import java.text.DateFormat  
import java.text.SimpleDateFormat  
import java.util.*  

fun main(){  
  var now = Date()  
  var sFormat : SimpleDateFormat  

  sFormat = SimpleDateFormat('yyyymmdd')  
  println(sFormat.format(now)) //202211115 형식 출력  

  sFormat = SimpleDateFormat("HH:mm:ss")  
  println(sFormat.format(now)) //22:10:31 형식 출력  
}

