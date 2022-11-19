## 과제를 하며 배운것
<br/>
<br/>

### 1. 화면 이동
<br/>
화면 이동은 onPressed 속성 안에 구현해요
<br/>
<br/>
stack으로 화면을 쌓아가는 구조에요
<br/>
<br/>
<strong>화면 이동하기</strong>
<br/>
<br/>

```
Navigator.push ( context, MaterialPageRoute ( builder: (context) => SecondPage()));
```
<br/>
<br/>
<strong>화면 빠져나오기</strong>
<br/><br/>

```
Navigator.pop ( context );
```
<br/><br/>
<strong>팁</strong>
<br/>
(1) onPressed 속성은 버튼안에서 구현되기 때문에<br/>화면 이동에 쓸 위젯을 TextButton 혹은 IconButton 등 버튼 위젯으로 구현하면 좋아요
<br/>
<br/>
(2) void main() 의 runApp() 내용을 바꿔줘야 해요<br/>const MyApp() 상태에서 전환을 하면 오류가 나요<br/>MaterialApp( home: MyApp() ) 으로 바꿔줘요
<br/>
<br/>
<br/>
### 2. 커스텀 위젯 활용하기
<br/>
stless 와 탭을 활용하여 커스텀위젯 트리거를 사용할 수 있어요
<br/><br/>
위젯 안에 사용하고자 하는 매개 변수를 선언하고 사용할 수 있어요
<br/> 예를 들면 <br/><br/>

```
const ErrandItem ( this.price, this.priceColor );
final String price;
final Color priceColor;
```
<br/>
이런 식으로 문자,숫자, 그리고 색깔 등을 매개변수로 활용하면 반복되는 UI를 쉽게 만들 수 있어요
<br/><br/>

## 강의를 보고 배운 것
<br/><br/>
### 1. FutureBuilder
<br/>
FutuerBuilder는 이용자의 미래 현황을 쉽게 결정하고 <br/><br/> 데이터를 불러올 때 어떤 것을 보여줄지 결정해요
<br/><br/> 예를 들면 로딩화면이 있어요 <br/>

```
FutureBuilder(
  future: http.get(url~),
  builder: (context, snapshot) {
  if(snapshot.connectionState ==
    ConnectionState.done) {
    return AwesomeData(snapshot.data);
   else return CircularProgressIndicator();
   }
  }
 )
 ```
<br/><br/>

### 2. LimitedBox
<br/>
LimitedBox 는 상위 요소의 제한을 받는 하위 위젯의 크기의 기본값을 설정할 수 있어요
<br/><br/> 즉, 상위 요소가 크기를 제한할 때 LimitedBox 에는 영향이 없어요 <br/><br/> ListView 와 함께 활용하면 자연스런 UI를 만들 수 있어요
<br/><br/>

### 3. Expanded
<br/>
대부분 위젯들은 행렬 형태로 정렬돼요 <br/> 위젯들을 나열할 때 Expanded 위젯을 사용하면 남은 공간을 자연스레 활용할 수 있어요
<br/>

```
Row(
  childern: [
    MyWidget(),
    Expanded(
      child: MyWidget()
      ),
     MyWidget(),
    ],
  )
```

<br/><br/>
### 4. Flexible
<br/>
Expanded 와 마찬가지로 위젯들은 행렬 형태로 정렬되고 부모 위젯 크기의 제한을 받아요
<br/><br/> 부모 위젯의 크기 변화에 따라 크기가 변하는 위젯을 원하면 Flexible 을 사용해요
<br/>

```
Column(children: [
  Flexible(
    flex: 2,
    child: Container(),
  ),
  Flexible(
    flex: 3,
    child: Container(),
  ),
  Flexible(
    flex: 1,
    child: Container(),
  ),
]);
```
<br/><br/> flex의 비율에 따라 크기가 변하고, fit 속성으로 세부 위치를 조정할 수 있어요
<br/><br/>

### 5. ListView
<br/>
앱에서 가장 많이 볼 수 있는 리스트뷰를 제공해요 <br/> scrollDirection으로 스크롤 방향을, reverse 속성으로 배치 방향을, physics 에서 스크롤 설정을 할 수 있어요
<br/><br/> 화면에 표시되지 않은 항목을 사용하지 않을거라면 AutomaticKeepAlive를 false로, 어느정도 제어를 하고싶다면 cacheExtent 속성을 사용해요
<br/><br/> 동적 리스트뷰가 필요하다면 ListView.builder()를, 간격을 주고싶다면 separatorBuilder를 사용해요 <br/><br/>

### 6. Spacer
<br/> Row 와 Column 위젯에서는 위젯 배치에 mainAxisAlignment 등을 활용해요 <br/><br/>
커스텀으로 배치를 원한다면 Spacer를 사용해요 <br/><br/> 위젯 사이에 Spacer()를 넣는다면 추가 공간을 위해 확장돼요 <br/> flex 속성도 활용할 수 있어요
<br/><br/>

### 7. SafeArea
<br/>
요즘 앱과 휴대폰은 직사각형으로 설계하지 않아요 <br/> 둥근 모서리같이 방해받는 요소를 해결하기 위해 SafeArea를 사용해요
<br/><br/>
먼저 MediaQuery로 화면과 가장자리 면적을 잰 후 앱의 화면을 맞춰줘요
<br/> 위젯에 감싸줘서 사용해요
<br/><br/>






