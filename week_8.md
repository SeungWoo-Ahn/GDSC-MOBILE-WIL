## Provider
### 1.Provider
<br/>
Provider는 <br/><br/>1) Flutter dev 공식 추천 <br/><br/>
2) 가장 보편적 <br/><br/> 3. Provider를 통한 Riverpod와의 연계할 수 있는 장점이 있어요 <br/><br/>

### 2. State management <br/><br/>
<strong>1) State 란?</strong> <br/><br/>
1. UI에 변화가 생기도록 영향을 미치는 데이터 <br/><br/>
2. 앱 수준의 데이터 + 위젯 수준의 데이터 <br/><br/>

<strong>2) State management란?</strong> <br/><br/>
1. 위젯이 쉽게 데이터에 접근할 수 있는 방법 <br/><br/>
2. 변화된 데이터에 맞춰 UI를 다시 그려주는 기능 <br/><br/>

<strong>3) setState method?</strong> <br/><br/>
1. Build method를 호출 <br/><br/>
2. Flutter가 기본 제공하는 state management <br/><br/>

<strong>4) setState method의 문제점</strong> <br/><br/>
1. 비효율성 => 한 개 위젯을 업데이트 할때마다 아래 모든 위젯을 다시 빌드해야해서 효율이 떨어져요 <br/><br/>
2. 동시에 다른 위젯의 state를 업데이트 시켜주지 못해요 <br/><br/>

### 3. Prodiver 사용법 <br/><br/>
1) 필요한 클래스 파일 생성, 변수 설정, 생성자 생성해요 <br/><br/>
2) 데이터를 필요로하는 위젯보다 상위에 Provider위젯으로 감싸요 <br/><br/>
3) Provider의 create 속성으로 사용할 클래스 (모델)을 설정해요 <br/><br/>

```
create: (context) => Model(name: ~, size:~), // 클래스 생성자
```

<br/><br/>
4) 하위 위젯에 필요한 부분에 클래스 변수를 불러와요

```
${Provider.of<Model>(context).name} // 모델의 name 데이터를 불러오는 예시
```
<br/><br/>
5) 데이터 변화에 따라 UI를 변경하기 위해 데이터 클래스에 ChangeNotifier를 mixin 해줘요 <br/>
but..  ChangeNotifier의 한계점
<br/><br/> 1. 매번 수동으로 addListener를 등록해주어야 해요 <br/><br/>
2. 수동으로 addListener를 제거해줘야 해요 <br/><br/>
3. 모델 인스턴스를 매번 생성자를 통해 전달해야 해요 <br/><br/>
4. UI 리빌드도 수동으로 해야 해요 <br/><br/>
6) 해결책 : ChangeNotifierProvider 사용 <br/><br/>
1. 모든 위젯들이 listen 할 수 있는 ChangeNotifier 인스턴스 생성 <br/><br/>
2. 자동으로 필요 없는 ChangeNotifier 제거 <br/><br/>
3. Provider.of 를 통해 위젯들이 쉽게 ChangeNotifier 인스턴스에 접근할 수 있어요 <br/><br/>
4. 필요시 UI 리빌드 해줄 수 있고, 필요 없다면 listen:false 기능 제공 <br/><br/>
7) Provider를 ChangeNotifierProvider 로 변경해요 <br/><br/>
8) 만약 여러가지 Provider가 필요하다면 MultiProvider를 사용 <br/><br/>providers: 속성으로 여러 Provdier 배열 사용 <br/><br/>

