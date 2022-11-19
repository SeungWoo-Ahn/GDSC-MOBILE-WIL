## FLUTTER 앱 개발 완성 - 4회차
<br/>

### 1. API <br/><br/>
<strong>API란?</strong>  <br/><br/>
API 는 다른 사람들이 내 컴퓨터에 있는 데이터에 접근할 수 있도록 만들어둔 기능을 API라고 해요 <br/><br/>

### 2. Dart에서의 비동기 <br/><br/>
<strong>동기와 비동기</strong>  <br/><br/>
1) 동기 (Synchronous) : 하나의 일이 끝난 뒤 다음 일을 하는 방식 <br/><br/>
2) 비동기 (Asynchronous) : 하나의 일이 끝나기 전에 동시에 다른 일을 하는 방식 <br/><br/>
API호출은 응답을 받기전 결과를 보여주는 비동기 방식이면 에러가 나요, 따라서 "동기" 방식으로 동작하는게 좋아요 <br/><br/>
![image](https://user-images.githubusercontent.com/78468001/202838763-eb5a1948-3b61-4097-b77e-2786880c16ca.png) <br/><br/>
위와 같은 문제를 해결하기 위해 비동기로 작동하는 코드를 동기 방식으로 실행하는 방법을 알아야해요 <br/><br/><br/><br/>

<strong>async 와 awiat</strong>  <br/><br/>
![image](https://user-images.githubusercontent.com/78468001/202839058-2db1c5e1-71dc-4848-b372-83331fd27363.png) <br/><br/>
1) async/await을 사용하는 함수는 반환값을 Future<T> 로 표시해요 (미래에 해당 타입을 반환한다는 의미) <br/><br/>
2) 해당 함수를 호출하는 경우에도 async와 await이 사용되며, await은 Future를 벗겨내는 역할을 해요 <br/><br/>
3) 예시 코드 <br/><br/>

  ```dart
  Future<String> getName() async {
	String name = await HTTP요청;
	return name;
}
```

<br/><br/>
<strong>비동기로 작동하는 상황들</strong>  <br/><br/>
1) 네트워크 요청하여 데이터 받아오기 <br/><br/>
2) 파일 읽기/ 쓰기 <br/><br/>
3) 데이터베이스 읽기/ 쓰기 <br/><br/><br/>
  
### 3. API 사용하기 <br/><br/>
<strong>Json 구조 파악</strong>  <br/><br/>
![image](https://user-images.githubusercontent.com/78468001/202839454-acbb2ee0-cd05-4a64-a4c7-2321b2af1881.png) <br/><br/>
url과 Json 구조를 보면서 원하는 데이터에 접근하기 위해 어떤 Key값을 사용해야하는지 확인해요 <br/><br/>

<strong>HTTP통신 패키지 dio 설치</strong>  <br/><br/>

```dart
  // API 호출 함수
  void getAPI() async {
    var result = await Dio().get(
      "api url",
    );
  }
```

<br/><br/>

<strong>불러온 Json파일을 객체 배열에 저장</strong>  <br/><br/>
1) 반복문을 돌며 Json 파일에 접근해요 <br/><br/>

```dart
  /// 검색어로 책 정보 불러오기
  void getBookList(String q) async {
    bookList.clear(); // 기존에 들어있는 데이터 초기화

    // API 호출
    Response res = await Dio().get(
      "https://www.googleapis.com/books/v1/volumes?q=$q&startIndex=0&maxResults=40",
    );
    List items = res.data["items"]; // items 접근
    for (Map<String, dynamic> item in items) {
      Map<String, dynamic> volumeInfo = item["volumeInfo"]; // volumeInfo 접근
      Book book = Book.fromJson(volumeInfo); // Map -> Book
      bookList.add(book); // Book 추가
    }

    // 화면 갱신
    notifyListeners();
  }
```
  
<br/><br/>
2) Map<K,V> 을 사용해 객체의 인스턴스 변수에 값을 할당해요 (factory 키워드는 생성자로 사용을 의미) <br/><br/>

```dart
    factory Book.fromJson(Map<String, dynamic> info) {
    return Book(
      title: info["title"] ?? "",
      subtitle: info["subtitle"] ?? "",
      thumbnail: info["imageLinks"]?["thumbnail"] ??
          "https://i.ibb.co/2ypYwdr/no-photo.png",
      previewLink: info["previewLink"] ?? "",
    );
  }
```
  
<br/><br/>

