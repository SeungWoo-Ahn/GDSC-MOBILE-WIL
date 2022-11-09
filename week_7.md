## RichText Class
<br/><br/>
애플리케이션에서 텍스트 및 타이포그래피는 중요해요 <br/><br/>
### 언제 사용할까요? <br/><br/>
1) 텍스트에 다양한 스타일을 결합하고 싶을 때 <br/><br/>
2) 특정 텍스트를 강조하기위해 bold 처리, 이탤릭체, 또는 밑줄을 긋고 싶을 때 <br/><br/>
3) 특정 텍스트에 다른 색이나 폰트를 적용하고 싶을 때 <br/><br/>

### 사용법 <br/><br/>

```
RichText (
  text : TextSpan( //기본적으로 TextSpan 위젯을 사용해요
    style: ... , // 여기에 공통으로 사용할 스타일을 지정해요
    children: <TextSpan> [
      TextSpan(text: '...'),
      TextSpan(text: '...' , style: ... ), //다른 스타일을 적용하고 싶은 텍스트에 스타일을 지정해요
      TextSpan(text: '...'),
    ],
  ),
),

```
<br/><br/>
Tip) TextSpan에 Gesture Recognizer 를 첨부하면 하이퍼 링크처럼 사용할 수도 있어요 <br/><br/>
![image](https://user-images.githubusercontent.com/78468001/200766153-ec5c0397-8d2c-4a3f-bcfd-6e07f19f0f90.png) <br/> 위젯 트리 구조 <br/><br/>
예시) [출처 : [https://iosroid.tistory.com/36](https://medium.com/@vappsxxx/ultimate-richtextguide-dynamically-add-textspan-to-richtext-6512c825f9e5)]<br/>
![image](https://user-images.githubusercontent.com/78468001/200767183-95beae67-5aca-4af0-bcba-e9d016f666ec.png) <br/><br/><br/><br/>
## 새로 알게된 것 <br/><br/>
### 1. 색상 ( 상수로 취급되는 값) 정리법 <br/><br/>
파일을 나눌때 공통으로 사용되는 값들 (색상, 텍스트 등등) 을 어떻게 관리해야 할지 고민이었어요 <br/><br/>
안드로이드에선 color.xml css에선 style.css 에 색상을 등록하고 사용해요 <br/><br/>
플러터에선 예를 들어 common 파일 > data 파일 > color.dart 에 색상을 const로 등록하고 각 파일마다 color.dart를 불러오는 방법을 사용하면 좋을 것 같아요 <br/><br/>
### 2. 새로 알게된 위젯 ListTile <br/><br/>
<strong>언제 사용할까요?</strong> <br/><br/>
재료 설계 사양에 맞추고 싶은 항목 리스트를 갖고 싶을때 <br/><br/>
<strong>어떻게 사용할까요?</strong> <br/><br/>

```
ListTile (
  leading: icon, //위젯의 제일 왼쪽 부분
  trailing : icon, //위젯의 제일 오른쪽 부분
  title : text, //위젯의 메인 텍스트
  subtitle: text, // 위젯의 서브 텍스트 (title 아래 위치)
  inThreeLine: bool, //세 줄로 구성할건지
  dense: bool, //밀집되게 텍스트를 배치할건지
  onTap, onLongPress // 눌렀을 때 구현되는 기능
  enabled : bool, // 사용 가능한지 여부
  selected: bool, //선택 되었는지 여부
);
```

<br/><br/> 리스트 뷰를 만들때 사용하면 좋을 것 같아요 <br/><br/>
<strong>예시</strong> <br/><br/>
![image](https://user-images.githubusercontent.com/78468001/200774330-bab47b83-da30-4a7c-9dfa-05b8f62e7ca3.png) <br/><br/>
### 3. 정리하고 싶은 위젯 GestureDetector <br/><br/>
<strong>언제 사용할까요?</strong> <br/><br/>
버튼이 아닌 특정 부분의 클릭 처리를 하고 싶을 때 <br/><br/>
<strong>어떻게 사용할까요?</strong> <br/><br/>

```
GestureDetector(
  child: childWidget(),
  onTap: , // 버튼과 비슷한 반응, 클릭 시
  onPanUpdate: , //Stack과 함께 드래그 가능한 위젯 생성 가능
  //그 외 더블클리, 긴 클릭, 스와이프, 확대 등 사용가능
)
```
<br/><br/>
onTap 속성이 버튼에만 있는줄 알았을 땐, TextButton과 IconButton을 억지로 끼워넣었는데 GetureDetector로 더 유연하게 UI를 짤 수 있어요
<br/><br/>
