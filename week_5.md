## FLUTTER 앱 개발 완성 - 1회차
<br/><br/>
### 1. Android Material & IOS Cupertino
<br/>
https://docs.flutter.dev/development/ui/widgets : flutter 위젯 공식문서
<br/><br/>
1) Material Widget: 안드로이드 스타일 위젯 <br/><br/>
2) Cupertino Widget: ios 스타일 위젯 <br/><br/>

### 2. 1주차 강의
<br/>
1) 위젯 래핑 단축키: ctrl + shift + r <br/><br/>
2) 입력 박스: TextField 위젯 사용: decoration에는 InputDecoration 사용, hint로는 labelText 속성 이용 <br/><br/>
  -1 decoration에는 InputDecoration 사용, hint로는 labelText 속성 이용 <br/><br/>
  -2 비밀번호처럼 가리고 싶은 정보: obscureText 속성 사용 <br/><br/>
3) Padding/ Margin 의 EdgeInset 에는 symmetric이라고 좌우 혹은 상하 여백을 설정할 수 있어요 <br/><br/>
4) Container 에는 margin 속성이 있어요 <br/><br/>
5) 웹에 있는 이미지 가져오기: Image.network 사용 <br/><br/>
6) 단일 스크롤뷰 사용: SingleChildScrollView <br/><br/>

### 3. Dart 문법
<br/>
https://dartpad.dev/?id=02d3c1600e40dd95d65af5ca6a3e4d16&null_safety=true : dart 연습 사이트
<br/><br/>
1) 변수
  -1 var: 처음 담은 값으로 자료형이 결정돼요 <br/><br/>
  -2 ? : 비어있을 수 있다  ex) String? email ==> null 가능 <br/><br/>
  -3 final : 값을 재할당 할 수 없어요. 상수 취급 <br/><br/>
  -4 bool : 참/거짓 <br/><br/>
  -5 split: 문자열을 자르는 String 내장함수 <br/><br/>
  -6 toInt, toDouble: 자료형 캐스팅 <br/><br/>
  -7 List<T> : ex) List<자료형> 이름 = [];, add/ remove 등 배열의 기본 함수들이 있어요 <br/><br/>
  -8 dynamic : 뭐든지 담을 수 있는 자료형 <br/><br/>
  -9 Map<K,V> : key와 value로 이루어진 자료구조 <br/><br/>
  
  ```
  Map<String, dynamic> person = {
    "name": "철수" , 
    "age": 20
  }
  ```
  <br/>
  
  -10 반복문 <br/>
  
  ```
  for (String name in fruits) {
    print(name);
  }
  //fruits 는 배열
  ```
  <br/>
  -11 함수 <br/><br/>
    이름 지정 매개변수: {} 안쪽에 전달을 선택할 수 있는 매개변수 <br/><br/>
    필수로 전달하는 매개변수: required 키워드를 사용 <br/><br/>
  
  ```
  void say({String? from, required String to}) {
    print("$from : 안녕? $to 야");
  }
  ```
  <br/>
  
  
  
  
  
