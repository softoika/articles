---
title: "Angular v14のstandalone componentsでコンポーネント単位の遅延読み込みが簡単になったっぽい"
emoji: "🎉"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["angular"]
published: false
---
## 要約
- ルーティング単位ではなくコンポーネント単位の遅延読み込み(lazy loading)
- standalone componentsは`NgModule`の働きも併せ持つ
- standalone componentsをdynamic importすることでリソースを遅延読み込み可能

## Angular v14で実装されたStandalone components
https://blog.angular.io/angular-v14-is-now-available-391a6db736af#0b75

## Standalone componentsで実現するコンポーネント単位の遅延読み込み
https://github.com/softoika/lazy-load-standalone-components

![lazyload](https://storage.googleapis.com/zenn-user-upload/2ecaa9741930-20220609.png)
![chunks](https://storage.googleapis.com/zenn-user-upload/62d988c1a8d6-20220609.png)

## Angular v13以前ではどう実現していたか
https://github.com/softoika/lazy-load-components

https://netbasal.com/welcome-to-the-ivy-league-lazy-loading-components-in-angular-v9-e76f0ee2854a
