# js-word-kana

JS における関数名や予約語のカタカナ一覧.

これは [クソアプリ Advent Calendar 2019](https://qiita.com/advent-calendar/2019/kuso-app)の 19 日目の記事である、[ビルド時に俳句を読めるプラグイン](https://qiita.com/sadnessOjisan/98619eaaef1da8d6545a) のために開発されたものです。

## 導入

```zsh
$ yarn add js-word-kana
```

```ts
const data: { [key: string]: string } = require("js-word-kana").default;
console.log(data)
{ import: 'インポート',
  require: 'リクワイアー',
  console: 'コンソール',
  break: 'ブレイク',
  // 中略
  setState: 'セットステート',
  ref: 'レフ',
  useState: 'ユーズステート',
  useEffect: 'ユーズエフェクト' }

```

## 開発

### 運用

モジュールインストール

```zsh
$ yarn install
```

本番用ビルド

```
$ yarn run build:prd
```

公開前にドライラン

```zsh
$ tar -tf $(npm pack)
```

npm に公開

```zsh
$ npm publish
```

### 辞書追加

1. 追加したいライブラリを src 配下に作成

```zsh
$ touch React.ts
```

2. key に関数名、value にカタカナを定義し export

各ライブラリの関数を見つけるために、 [pubget](https://github.com/sadnessOjisan/pubget) というツールを開発したので、こちらもご利用ください。

```ts
export default {
  React: "リアクト",
  props: "プロップス",
  componentDidMount: "コンポーネントディドマウント",
  state: "ステート",
  setState: "セットステート",
  ref: "レフ",
  useState: "ユーズステート",
  useEffect: "ユーズエフェクト",
};
```

3. main.ts で それぞれ import し、平たいオブジェクトにして export

```ts
export default {
  // 中略
  ...React,
};
```
