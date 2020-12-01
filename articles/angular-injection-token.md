---
title: "[Angular小ネタ] InjectionTokenを使ってService以外の値をDIする"
emoji: "💉"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["angular"]
published: false
---
<!-- InjectionTokenを使えばstringやbooleanなどの値もDIできるようになって、テスト書きやすくなるよという話 -->
AngularのDI(Dependency Injection, 依存性の注入)機能はComponent/Service/Directive/Pipeなどを疎結合に書くためには欠かせない重要な要素です。
Angularの公式ドキュメントでもHeroServiceに`@Injectable`デコレータを指定することでServiceを注入している例があります。[[1]](https://angular.jp/guide/dependency-injection)
こうすることで外部にHTTPリクエストを投げるServiceをテスト時にはモックに置き換えることができます。
コンストラクタに直接渡す以外にもTestBedで`useValue`/`useClass`/`useFactory`を使ったプロバイダーを指定することでも置き換えられます。

Serviceなどの`@Injectable`デコレータが付いたclassを注入のは上記の方法で簡単にできるのですが、外部の関数や`boolean`や`string`などの値を注入するにはどうすればいいのか気になったので調べてみました。
