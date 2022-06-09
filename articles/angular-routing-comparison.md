---
title: "[Angular] RouterとrouterLinkはどのように使い分けるべきか"
emoji: "⚖️"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["angular"]
published: false
---
## Angularでナビゲーションする方法は2通りある
Angularでナビゲーションする方法は、コンポーネントのコードから`router.navigate()`により実現する方法と`routerLink`ディレクティブにより実現する方法の２通りがあります。
<!-- この記事では、アクセシビリティやパフォーマンスの観点で`routerLink`により実現する方がいかに好ましいかについて紹介します。 -->

ご存じの方も多いと思いますが、まずは簡単に各方法について見ていきましょう。

<!-- ### `router.navigate()` -->
### `Router`
[`router.navigate()`](https://angular.jp/api/router/Router#navigate)はコンポーネントなどに`Router`をインジェクトすることによって使える方法です。
私の記憶が正しければ、過去のAngular公式ドキュメントにはこちらの方法も記載されていたと思います。
ナビゲーション先が動的な場合やナビゲーション時の追加処理が書きやすいという理由でこちらを使っている人もいるかもしれません。
```ts
@Component({
  /* ... */
})
export class AppComponent {
  constructor(private router: Router) {}

  navigate() {
    this.router.navigate(['/router-navigate']);
  }
}
```
```html
<a (click)="navigate()">router.navigate()</a>
```

### `routerLink`
[`routerLink`](https://angular.jp/api/router/RouterLink)はディレクティブとしてコンポーネントやHTML要素に指定することでナビゲーション先を指定する方法です。
現在の[公式チュートリアル](https://angular.jp/tutorial/toh-pt5#%E3%83%8A%E3%83%93%E3%82%B2%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%81%AE%E3%83%AA%E3%83%B3%E3%82%AF%E3%82%92%E8%BF%BD%E5%8A%A0%E3%81%99%E3%82%8B-routerlink)ではこちらの方法のみ記載されているようです。(以前から?)
```html
<a routerLink="router-link">routerLink</a>
```
## `routerLink`が好ましい理由
### アクセシビリティ面
https://developer.mozilla.org/ja/docs/Web/HTML/Element/a#onclick_%E3%82%A4%E3%83%99%E3%83%B3%E3%83%88
### ngx-quicklinkとの相性
https://github.com/mgechev/ngx-quicklink

## どのようなときに`router.navigate()`を使うべきか
暗黙的な画面遷移。例えばsubmit後のナビゲーションなど
見た目がボタンなリンクを使うべきか？

## 動作環境
最後にこの記事が前提とする動作環境を載せておきます。

- Angularのバージョン: 13.3.7

- GitHub:

https://github.com/softoika/routing-comparison

- StackBlitz:

https://stackblitz.com/github/softoika/routing-comparison?file=src%2Fapp%2Fapp.component.ts
