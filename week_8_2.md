## FLUTTER 앱 개발 완성 - 3회차
###  1. 패키지란? <br/><br/>
다른 사람들이 만들어 둔 위젯 또는 기능들을 <strong>패키지</strong>라 불러요 <br/><br/>
안드로이드에서 라이브러리를 사용하는 것과 비슷해요 <br/><br/>
Flutter 에서 쓰는 패키지 검색 [https://pub.dev/] <br/><br/>
다른 사이트<br/> [https://github.com/Solido/awesome-flutter#ui] <br/> [https://fluttergems.dev/] <br/><br/>
적용법은 설치는 Installing 탭에서, 사용은 Readme 와 Example 탭에서 확인 할 수 있어요 <br/><br/>
### 2. SharedPreferences <br/><br/>
SharedPreferences 는 기기에 파일로 저장해두고 앱을 시작할 때 파일을 읽어오는 방식이에요<br/><br/>
패키지로 사용할 수 있어요 [https://pub.dev/packages/shared_preferences] <br/><br/>
<strong>사용법</strong> <br/><br/>
1) 인스턴스를 불러와요 <br/><br/>

```dart
void main() async {	
	// main() 함수에서 async를 쓰려면 필요
  WidgetsFlutterBinding.ensureInitialized();

  // shared_preferences 인스턴스 생성
  SharedPreferences prefs = await SharedPreferences.getInstance();

```

<br/><br/>

2) 전역변수로 추가해요 <br/><br/>

```dart
// SharedPreferences 인스턴스를 어디서든 접근 가능하도록 전역 변수로 선언
late SharedPreferences prefs;
```

<br/><br/>

3) set과 get을 활용해서 사용해요<br/><br/>

```dart
	
// Done 클릭시 isOnboarded = true로 저장
prefs.setBool("isOnboarded", true);

// SharedPreferences에서 온보딩 완료 여부 조회
// isOnboarded에 해당하는 값에서 null을 반환하는 경우 false 할당
bool isOnboarded = prefs.getBool("isOnboarded") ?? false;
```

<br/><br/>

4) 더 이상 필요하지 않다면 삭제해요<br/><br/>

```dart
// SharedPreferences에 저장된 모든 데이터 삭제
prefs.clear();
```

<br/><br/>
### 3. AlertDialog
<br/><br/>
앱에는 팝업 화면 즉 모달창이 필요한데 이때 AlertDialog를 사용해요 <br/><br/>
<strong>사용법</strong> <br/><br/>
1) showDialog 내장함수를 이용해서 context를 받아와요, 이때 사용되는 context는 BuildContext에요<br/><br/>
2) builder: 속성 내부에 AlertDialog를 return 해줘요<br/><br/>
3) AlertDialog의 title 및 actions 속성을 이용해 기능을 구현해줘요 <br/><br/>
4) 예시 <br/><br/>

![image](https://user-images.githubusercontent.com/78468001/202386213-76fe3d7f-aa0b-494a-bac9-c6427365ae05.png) <br/><br/>

### 4. TabBarView
<br/><br/>
위젯을 탭에 넣어서 사용해야 할 때, TabBar와 TabBarView를 사용할 수 있어요 <br/><br/>
<strong>사용법</strong>   <br/><br/>

```dart
home: DefaultTabController( //선택 탭과 콘텐츠를 동기화하려면 필요한 탭 컨트롤러
  length: //(int) 탭 개수,
  child: Scaffold(
    appBar: AppBar(
      bottom: TabBar(
        tabs: [
          Tab(), //탭에는 아이콘이나 위젯을 사용할 수 있어요
          Tab(),
          Tab(),
        ],
      ),
    ),
  ),
);
```
<br/><br/>

```dart
TabBarView(
  children: [
    Container(), //하위 목록에 포함된 각 위젯은 TabBar의 탭에 해당해요
    Container(),
    Container(),
  ],
),
```
<br/><br/>


