# go_router_memo
- go_routerのネストの仕組みについて記録しておく
  - go_routerは戻るボタンがAppBarにない?
  - ルートネストさせると戻るボタンは現れる
  - アプリの最初のルートは、/をつけないとエラーを吐く!
  - go_router: ^6.0.5から、Pathの指定で、/を最初のページ以外はつけなくてよくなった?


```dart
import 'package:sugary_map/service/export/router_export.dart';

final router = GoRouter(
  initialLocation: '/sign_in',
  routes: [
    GoRoute(
      name: SignInPage.routeName,
      path: '/sign_in',
      builder: (context, state) => SignInPage(),
      routes: [
        GoRoute(
          name: SignUpPage.routeName,
          path: 'sign_up',
          builder: (context, state) => SignUpPage(),
          routes: [
            GoRoute(
              name: UserSignupPage.routeName,
              path: 'user_sign_up',
              builder: (context, state) => UserSignupPage(),
            ),
            GoRoute(
              name: ShopSignupPage.routeName,
              path: 'shop_sign_up',
              builder: (context, state) => ShopSignupPage(),
            ),
          ],
        ),
      ],
    ),
  ],
);

```
