# 첫 주차 만들면서 배운것

## 1. 폰트 적용
</br>
</br>

1. assets/font 에 원하는 폰트를 저장해요</br>
2. pubspec.yaml 에 저장한 폰트를 등록해요 </br>
```
  fonts:
    - family: Asac
      fonts:
        - asset: assets/font/ChangwonDangamAsac.ttf
          weight: 700
```
3. 원하는 텍스트에 fontFamily 에 등록한 폰트명을 입력해요</br></br>

## 2. margin 대용으로 쓸 수 있는 것
</br>
margin 은 필요한 경우가 많아요</br>
Margin() 위젯도 있지만 SizedBox() 위젯의 width, height를 이용하면 margin 처럼 활용할 수 있어요
</br>
</br>

## 3. BoxDecoration
</br>
1. 모서리 둥글게 하기 위해선 BorderRadius.circular()를 사용해요</br>
2. 그림자 효과는 BoxShadow() 를 사용해요</br>
```
boxShadow: const [
  BoxShadow(
    color: Color(0xffbbc1d0),
    spreadRadius: 3,
    blurRadius: 3,
    offset: Offset(0, 3),
  )
]
```
<br/>
3. 모서리 색과 굵기는 Border() 를 사용해요<br/>
```
border: Border.all(
  width: 1,
  color: Color(0xfff1f1f1),
  )
```
<br/><br/>

## 4. Stack() 과 이미지
<br/>
Stack() 은 위젯들을 중첩하기 위해 <br/>
이미지 채움을 결정하기 위해선 fit을 사용해요<br/>
BoxFit.fill 은 크기를 꽉 채우게 해줘서 가장 흔히 쓰여요
<br/><br/>

## 5. Row() 와 Column()
<br/>
mainAxisAlignment 와 crossAxisAlignment 를 잘 이용하면 UI를 쉽게 구성할 수 있어요<br/>
spaceBetween 과 spaceEvenly 는 css 의 flex와 유사해요<br/><br/>

## 6. ListView()
<br/>
스크롤 화면을 만들어주는 ListView() 는 scrollDirection을 통해 방향을 지정할 수 있어요<br/>
Axis.horizontal 로 가로 스크롤 화면을 만들 수 있어요 <br/>
스크롤 바 숨기는 법<br/>

```

class NoThumbScrollBehavior extends ScrollBehavior {
  @override
  Set<PointerDeviceKind> get dragDevices => {
        PointerDeviceKind.touch,
        PointerDeviceKind.mouse,
        PointerDeviceKind.stylus,
      };
}

```
이후 scrollBehavior: NoThumbScrollBehavior().copyWith(scrollbars: false) 설정해요
<br/><br/>

## 7. 앱 바의 텍스트 중앙으로
<br/>
centerTitle: true 로 설정하면 텍스트가 중앙에 배치돼요
<br/><br/>

                  
