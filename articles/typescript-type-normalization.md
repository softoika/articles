---
title: "[TypeScript] 型の正規化をしよう(仮)"
emoji: "⚙️"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["typescript"]
published: false
---
## アイデア
```ts
interface Hoge {
  foo: number;
  bar: boolean;
  baz: string;
}
```
のような型があったときに
```ts
function getFooFromHoge(): number;
```
のような型を書くのではなく
```ts
function getFooFromHoge(): Hoge['foo'];
```
と書くことで同じような型定義を色んな箇所に散在させるのを防ごうという内容の記事。

他にも
```
import { Hoge } form './hoge';
interface Fuga {
  hoge: Hoge;
}
```
しているような型があるときに、他のファイルの関数で
```
function getHogeFromFuga(): Hoge;
```
するよりかは
```
function getHogeFromFuga(): Fuga['hoge'];
```
した方が、型のimport/export先が限定されるので型定義の変更が用意になるし、バンドルサイズ削減にもつながる(?要調査)かもね。
というメリットがある

TypeScriptには`type`による型エイリアスもあるので、こういった特定の型の持つプロパティの型を間接的に参照するというやり方がやりやすい印象。
