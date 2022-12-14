# Flutter with GetX
<br/><br/>
## 1. GetX 란?
<br/><br/>
모든 것이 Widget으로 이루어진 Flutter에서 상태 관리를 위해 사용되는 대표적인 라이브러리가 <strong>GetX</strong>이에요 <br/><br/>
GetX와 함께 요즘 잘 쓰이는 RiverPod과 Bloc도 있다고 해요 <br/><br/>
GetX는 매우 가볍고 강력한 솔루션이고 고성능 상태 관리, 지능형 종속성 주입, 라우트 관리 기능을 제공해요 <br/><br/>
특징 <br/>
1) Streams, ChangeNotifier를 사용하지 않아요 <br/><br/>
2) 사용하지 않는 리소스는 메모리에서 자동으로 제거해줘요 <br/><br/>
3) 화면, 프레젠테이션 로직, 비지늬스 로직, 종속성 주입, 네비게이션을 완전히 분리할 수 있어요 <br/><br/><br/>
## 2. bindStream
<br/><br/>
Stream은 다트에서 비동기 처리를 하는 방식 중 하나에요. <br/><br/>
대표적으로 Stream과 Future를 활용하는데, Future는 즉시 완료되지 않는 계산을 나타내요. 비동기 함수는 Future를 반환하여 결과에 포함되고 결과가 준비되면 Future에 알려줘요 <br/><br/>
Stream은 계속해서 데이터의 변화를 감지하고 그에 맞춰 적절한 처리를 할 때 사용해요 <br/><br/>
bindStream은 FirebaseAuth 와 Flutter프로젝트를 연동할 때 사용했어요 <br/><br/>

```dart
class AuthController extends GetxController {
  static AuthController get to => Get.find();
  Rxn<User> firebaseUser = Rxn<User>();
  Rxn<UserModel> firestoreUser = Rxn<UserModel>();
  RxBool isLoggedIn = false.obs;

  @override
  void onReady() {
    // TODO: implement onReady
    super.onReady();
    //run every time auth state changes
    ever(firebaseUser, handleAuthChanged);
    firebaseUser.bindStream(user);
  }

  handleAuthChanged(_firebaseUser) async {
    //get user data from firestore
    if (_firebaseUser?.uid != null) {
      firestoreUser.bindStream(streamFirestoreUser());
    }
    if (_firebaseUser == null) {
      Get.offAll(() => LoginPage());
    } else {
      Get.offAll(() => HomePage());
    }
  }

  //Streams the firestore user from the firestore collection
  Stream<UserModel> streamFirestoreUser() {
    print('streamFirestoreUser()');

    return firebaseFirestore
        .doc('/users/${firebaseUser.value!.uid}')
        .snapshots()
        .map((snapshot) => UserModel.fromMap(snapshot.data()!));
  }

  // Sign out
  Future<void> signOut() {
    return auth.signOut();
  }
}
```

<br/><br/><br/>
## 3. ever
<br/><br/>
GetX에는 workers란 특별한 기능이 있어요. workers를 사용하면 Rx변수들을 감지하고 다양한 상황 별로 적절한 대응을 할 수 있어요 <br/><br/>
그 중 ever는 변수가 변경될 때만 호출돼요. 가장 많이 쓰일 것 같아요 <br/><br/>
once는 처음으로 변경되었을 때만 호출돼요. <br/><br/>
debounce는 변수가 변경되다가 마지막 변경 후, n초간 변경이 없을 때 호출돼요. 이 n초는 duration을 이용해 설정할 수 있어요 <br/><br/>
interval은 변수가 변경되고 있는 동안, n초마다 호출돼요. 마찬가지로 duration을 이용해 설정할 수 있어요
<br/><br/><br/>
## 4. Rxn, Rx, .obs
<br/><br/>
Obx는 단순 상태 관리에 비해 다소 복잡해요 <br/><br/>
그래서 반응형 상태관리를 사용할 수 있는데 그 방법으론 Rxn, Rx, .obs 이 있어요 <br/><br/>
### 1) Rxn <br/><br/>

```dart
// 초기값을 설정하는 것을 추천하지만, 필수는 아닙니다.
final name = RxString('');
final isLogged = RxBool(false);
final count = RxInt(0);
final balance = RxDouble(0.0);
final items = RxList<String>([]);
final myMap = RxMap<String, int>({});
```

<br/><br/>

### 2) Rx <br/><br/>

```dart
final name = Rx<String>('');
final isLogged = Rx<Bool>(false);
final count = Rx<Int>(0);
final balance = Rx<Double>(0.0);
final number = Rx<Num>(0);
final items = Rx<List<String>>([]);
final myMap = Rx<Map<String, int>>({});

// 커스텀 클래스 - 그 어떤 클래스도 가능합니다
final user = Rx<User>();
```

<br/><br/>

### 3) .obs <br/><br/>

```dart
final name = ''.obs;
final isLogged = false.obs;
final count = 0.obs;
final balance = 0.0.obs;
final number = 0.obs;
final items = <String>[].obs;
final myMap = <String, int>{}.obs;

// 커스텀 클래스 - 그 어떤 클래스도 가능합니다
final user = User().obs;
```

<br/><br/>
이 중 흔히 사용하는 방법은 .obs 방법이라고 해요 <br/><br/>
Obx()는 내부에 포함된 모든 observable을 모니터링하여 변경된 것을 감지하여 업데이트 해요

<br/><br/><br/>
## 5. GetX Navigation
<br/><br/>
Navigation은 라우트 관리를 해요. 기존의 flutter에선 MaterialPageRoute를 사용했는데 context를 담아줘야하는 단점이 있어요 <br/><br/>
하지만 GetX는 context없이 다양한 기능을 활용하며 라우트 관리를 할 수 있어요 <br/><br/>
1) Get.to() : 새로운 화면으로 이동해요<br/><br/>
2) Get.toNamed() : GetMaterialApp에 getPages 속성에 정의해둔 이름의 화면으로 이동해요<br/><br/>
3) Get.back() : 이전 화면으로 돌아가요<br/><br/>
4) Get.off() : 다음 화면으로 이동하면서 이전 화면을 없애요, offNamed()로도 사용 가능해요<br/><br/>
5) Get.offAll() : 다음 화면으로 이동하면서 이전 화면 전부를 없애요<br/><br/>


Navigation엔 추가적인 기능들이 있는데, <br/><br/>
1) argument : 라우트에 데이터를 태워서 보낼 수 있어요 <br/><br/>

```dart
Get.toNamed("/first", arguments: DTO(name: "안승우", num: 26));
```

<br/><br/>

2) transtion: 화면 전환 속성을 정의할 수 있어요 <br/><br/>

```dart
enum Transition {
  fade,
  fadeIn,
  rightToLeft,
  leftToRight,
  upToDown,
  downToUp,
  rightToLeftWithFade,
  leftToRightWithFade,
  zoom,
  topLevel,
  noTransition,
  cupertino,
  cupertinoDialog,
  size,
  native
}
```


<br/><br/><br/>

