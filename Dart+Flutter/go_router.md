# <p align="center">`Go_router.package`</p>

## 👍 장점

1. `deeplink` 지원
2. flutter Dev 지원
3. 중첩 path 지원(`name` 별칭 사용가능)
4. Redirect & Refresh & error 핸들링
5. 기존 웹 기반 라우팅 라이브러리와 같은 방식으로 제공

## 📝 한 달 후기

1. 코드 가독성이 좋아진다

```dart
// 기존 flutter router
MaterialPageRoute(builder: (_) => const PenInjAfterWaitingTimeScreen(), settings: settings);
Navigator.push(context,CupertinoPageRoute(builder: (context) => const SecondRoute()))},

// go_router package
GoRoute(path: '/', builder: (_, state) => const Home());
...
onTap: () => context.go('/page2')
```

## 🌅 Installing

```bash
$ flutter pub add go_router
```

```bash
import 'package:go_router/go_router.dart';
```

### 📍기본 path 정의

`GoRoute(path: path이름, builder: (_, state) => 이동할 목적지)`

```dart
final GoRouter _router = GoRouter(
    initialLocation: '/',
    //기본 경로 설정
    routes: [
      //라우트 정의
      GoRoute(path: '/', builder: (_, state) => const Home()),
      GoRoute(path: '/login', builder: (_, state) => const Login()),
...
```

```dart
@override
  Widget build(BuildContext context) {
    return MaterialApp.router(
		  // The route information provider used by [GoRouter].
      routeInformationProvider: _router.routeInformationProvider,
		  // The route information parser used by [GoRouter].
      routeInformationParser: _router.routeInformationParser,
      routerDelegate: _router.routerDelegate,
    );
  }
```

### 🌄 initialization

```dart
late final _router = GoRouter(
  routes: _routesBuilder,
  error: _errorBuilder,
  initialLocation: '/page2',
);
```

## 💡`go_router` 메소드

- `go()` 스택이 쌓이지 않음 (뒤로가기 버튼 X)
  ```dart
  context.go('/login');
  ```
- `goNamed()`
  ```jsx
  context.goNamed(routeName);
  //route에 선언한 name으로 이동합니다
  ```
- `pushNamed()` 스택이 쌓임 (뒤로가기 버튼O)
  ```jsx
  context.pushNamed(routeName);
  ```

### \***\*Child routes\*\***

```dart
GoRoute(path: '/setting', builder: (_, state) => const Setting(), routes: [
        GoRoute(
            path: "first",
            name: 'first',
            //goNamed 사용을 위한 이름
            builder: (_, state) => const First(),
            routes: [
              GoRoute(
                path: "second",
                name: 'second',
                builder: (_, state) => const Second(),
              )
            ]),
      ]),
// /setting/first/second로 이동할 수 있음
```

### `pop()` ← 뒤로가기

```dart
ElevatedButton(
        onPressed: () {
          context.pop();
        },
        child: const Text('(pop)')),
```

### **경로에서 매개변수 전달 받기**

```dart
GoRoute(
        path: '/',
        name: rootRouteName,
        builder: (context, state) {
          return HomeScreen(tab: 'shopping');
        },
      ),
```

### 경로의 매개변수 받기

```dart
GoRoute(
        path: '/:tab',
        name: rootRouteName,
        builder: (context, state) {
          final tab = state.params['tab'];
          return HomeScreen(tab: tab ?? '');
        },
      ),
```

### QueryParams 전달하기

```dart
child: ElevatedButton(
  onPressed: () => context.goNamed("settings", params: {
    "name": "HongGilDong"
  }, queryParams: {
    "email": "gildong@gmail.com",
    "age": "25",
    "place": "SouthKorea"
    }),
    child: const Text("Go to Settings page"),
),

// --

GoRoute(
  name: "settings",
  path: "settings/:name",
  builder: (context, state) {
    state.queryParams.forEach(
      (key, value) {
        print("$key:$value");
       },
     );
   return SettingsPage(
     name: state.params["name"]!,
   );
 },
)
```

### Error builder 404

```dart
final GoRouter _router = GoRouter(
  errorBuilder: (context, state) => const ErrorScreen(),
);

//---

class ErrorScreen extends StatelessWidget {
  const ErrorScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        automaticallyImplyLeading: true,
        title: const Text("Error Screen"),
      ),
      body: Center(
        child: ElevatedButton(
          onPressed: () => context.go("/"),
          child: const Text("Go to home page"),
        ),
      ),
    );
  }
}
```

### Redirect

```dart
final GoRouter _router = GoRouter(
  routes: [
    GoRoute(
      name: "home",
      path: "/",
      builder: (context, state) => const HomePage(),
      redirect: (context, state) {
        if (userIsNotLoggedIn){
          return "/login"
        }
        return "/"
      },
    ),
  ],
  errorBuilder: (context, state) => const ErrorScreen(),
);
```

### **ShellRoute**

- 기존경로를 ShellRoute로 래핑

```dart
inal GlobalKey<NavigatorState> _rootNavigatorKey =
    GlobalKey<NavigatorState>();

  final GoRouter _router = GoRouter(
    navigatorKey: _rootNavigatorKey,
    initialLocation: '/a',
    routes: [
      ShellRoute(
        navigatorKey: _shellNavigatorKey,
        builder: (context, state, child) {
          return ScaffoldWithNavBar(child: child);
        },
        routes: [
          // This screen is displayed on the ShellRoute's Navigator.
          GoRoute(
            path: '/a',
            builder: (context, state) {
              return const ScreenA();
            },
...
```
