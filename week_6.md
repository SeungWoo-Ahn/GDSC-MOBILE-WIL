## FLUTTER 앱 개발 완성 - 2회차
<br/><br/>
### 1. Flutter Widget 이해
<br/><br/>
모든 위젯은 StatelessWidget과 StatefulWidget으로 나눌 수 있어요 <br/><br/>
1) StatelessWidget : 상태 변화가 없는 위젯 <br/><br/>
![image](https://user-images.githubusercontent.com/78468001/199254574-2d7ff1be-cf83-40d9-b85a-1e3a4aa83a03.png)
<br/><br/>
2) StatefulWidget : 상태 변화가 있어 화면을 새로고침 할 필요가 있는 위젯 <br/><br/>
![image](https://user-images.githubusercontent.com/78468001/199254908-c17854a6-eab5-4f0f-98e9-3552f66f8af6.png)
<br/><br/> setState() 로 화면 갱신하며 해당 위젯을 다시 호출해요 <br/><br/> 
### 2. 화면을 만드는데 필요한 기능
<br/><br/>
1) Container의 BoxShadow <br/><br/>
withOpacity() : 투명도를 줘요 <br/><br/>
spreadRadius : 퍼짐 효과를 줘요 <br/><br/>
blurRadius : 뭉갬 효과를 줘요 <br/><br/>
offset: Offset() : 그림자를 이동해요 <br/><br/>
2) BottomNavigation 의 속성들 <br/><br/>
currentIndex : 현재 선택된 메뉴를 설정해요 <br/><br/>
selectedItemColor : 선택된 메뉴 색깔을 설정해요 <br/><br/>
3) Positioned 위젯으로 Stack 내부에서 원하는 위치에 배치할 수 있어요 <br/><br/>
4) SingleChildScrollView 는 스크롤 하는 화면을 만들어줘요 <br/><br/>
5) TextField 위젯 속성들 <br/><br/>
autofocus : 자동 포커스 (bool) <br/><br/>
onChanged : (text) {} : 텍스트 변경시 실행되는 함수 <br/><br/>
onSubmitted : (text) {} : Enter를 누를때 실행되는 함수 <br/><br/>
6) 화면 이동 : 각 화면을 라우트(Route)라고 부르며, 화면을 이동할 때 네비게이터를 사용해요 <br/><br/>
다음 페이지로 이동하기 <br/><br/>

```
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => SecondPage()), // 이동하려는 페이지
);
```
<br/><br/>
현재 화면 종료 <br/><br/>

```
Navigator.pop(context); // 종료
```
<br/><br/>
7) Tip <br/><br/>
Material Icon 사이트 : https://fonts.google.com/icons?selected=Material+Icons <br/><br/>
Cupertino Icon 사이트 : https://shuuji3.xyz/flutter-packages/third_party/packages/cupertino_icons/ <br/><br/>
AppBar의 영역에 대한 명칭 <br/><br/>
![image](https://user-images.githubusercontent.com/78468001/199276367-9f72e448-cb34-434d-bad6-0c395e197324.png) <br/><br/>
에러가 난 곳의 Quick Fix : ctrl + . <br/><br/>
asset 파일 모두 불러오기 <br/><br/>
![image](https://user-images.githubusercontent.com/78468001/199276703-c3a2ad40-0009-4a06-858d-208179efcb31.png)





