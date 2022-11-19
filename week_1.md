# Flutter 시작하기


### 1. 기본 위젯 4개

(참고) Lint 끄는 법
<br/>
<br/>
analysis_options.yaml 에 작성
<br/>
<br/>

```
rules:
  prefer_typing_uninitialized_variables : false
  prefer_const_constructors_in_immutables : false
  prefer_const_constructors : false
  avoid_print : false
```

<br/>

1. 글자 위젯
```
Text('글 내용')
```
<br/>

2. 아이콘 위젯
```
Icon(Icons.아이콘 이름)
```
<br/>

3. 이미지 위젯
```
Image.asset('경로')
```
<br/>

4. 네모 박스 넣을 땐
```
Container()
```
<br/>
<br/>


### 2. 가로세로 배치와 Scaffold
<br/>
<br/>
1. 상중하로 나눠주는 Scaffold() 위젯
<br/>
appBar, body, bottomNavtigationBar 로 기본 앱 구조로 나눠준다
<br/>
<br/>
2. 여러 위젯 가로로 배치
<br/>

```
Row( children: [] )
```
<br/>
mainAxisAlignment 로 현재 방향으로 위젯 배치를 설정할 수 있다
<br/>
crossAxisAlignment 로 반대 방향으로 위젯 배치를 설정할 수 있다
<br/>
이는 Column 을 사용해도 동일
<br/>
<br/>
3. 여러 위젯 세로로 배치
<br/>

```
Column( children: [])
```
<br/>
팁 : ctrl + space 누르면 사용 가능한 속성들이 보인다
<br/>
<br/>

### 3. 박스 디자인
<br/>
Container() 안에 width, height, color 등 속성을 지정할 수 있다
<br/>
여백은 margin과 padding 을 이용해 EdgeInsets 으로 설정할 수 있다
<br/>
이 외 세부 디자인은 decoration : BoxDecoration() 을 이용해 설정할 수 있다
<br/>
정렬은 Align() 로 감싸고 alignment 속성으로 배치할 수 있다
<br/>
팁 : Container() 등을 감싸고 싶으면 클릭 후 왼쪽 전등 아이콘 클릭
<br/>
<br/>

### 4. 앱 바
<br/>
참고 : 글자와 아이콘 스타일은 각 위젯 안에 style속성으로 지정할 수 있다
<br/>
<br/>
참고 : 버튼은 TextButton(), ElevatedButton(), IconButton() 활용
<br/>
내부엔 child 와 onPressed 속성이 무조건 포함되어야 한다
<br/>
<br/>
AppBar()에는 다음과 같은 것들을 넣을 수 있다
<br/>

1. title: 왼쪽 제목

2. leading: 왼쪽에 넣을 아이콘

3. actions:[ 우측 아이콘들 ]

<br/>
<br/>

### 5. Flexible()
<br/>
화면을 원하는 비율로 나누고 싶을 때 사용한다
<br/>
사용법: 
<br/>

1. Row() 혹은 Column 안 children 에 Flexible() 위젯을 넣는다

2. Flexible() 에 원하는 children을 넣고, 뒤에 flex속성을 활용해 비율을 설정한다

3. 나머지 공간을 꽉 채우고 싶다면 Flexible 대신 Expanded()를 사용한다

<br/>
<br/>

### 6. 커스텀 위젯 사용하기
<br/>
팁 : stless 입력후 tab을 누르면 기본 함수 구조가 나온다
<br/>
위젯을 한 단어로 축약하려면
<br/>

1. class 작명

2. return 옆에 축약할 레이아웃 넣기

3. 사용하고 싶은 위치에 클래스 넣기

<br/>
다른 방법: var 변수명 = 에 작성해도 되지만
<br/>
성능 이슈가 발생할 수 있으므로, 자주 변하지 않을 앱 바 혹은 네비게이션에만 사용
<br/>
<br/>
출처 : 유튜브 코딩애플 [쉽게 알려주는 플러터 강의임]







