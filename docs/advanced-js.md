# ページ内に動きをつけよう
ページに動きをつけたいときはJavaScriptを使いましょう
## JavaScriptについて
`JavaScript`(以下`JS`とする)は主にブラウザ上のウェブサイトで`HTM`Lを操作したりするのに使われています.
また、サーバーサイドで使われることもあります.
`JS`の仲間として`TypeScript`(`TS`)もあり、`TS`は`JS`に型を付けた言語です.
[もっと詳しい情報を見る](https://developer.mozilla.org/ja/docs/Web/JavaScript)
## JSを書いてみる
では実際にJSを書いてみましょう.
JSを書くと言っても、新しくファイルを作成する必要はありません。
JSを試す最も簡単な方法はブラウザを使う方法です。

**以下はChromeを使ってJSを書く方法です**
1. ブラウザで開いた任意のページ上で右クリックを押す
2. `検証`ボタンを押す
3. 開発者ツールが開くので開発者ツールの上側にある`Console`ボタンを押す
4. `Console`が開くので、以下のように入力してください
   ```JavaScript
   console.log("Hello, world")
   ```
5. `Enter`キーを押す
6. `Hello, world`と出力されたはずです. おめでとうございます！🥳 ここがJSの入り口です！

## もっとJSを乗りこなす
このコンテンツの名前を覚えていますか？  
そう、**ページ内に動きをつけよう** です.  
`ページに動きをつける = JSを乗りこなす` ことによってあなたの作品はもっと素晴らしいものになるでしょう!!
### `document.body`
```JS
const body = document.body;
```
このとき`body`はHTMLの`<body>`タグ自体とその中の要素全てを表しています.

### 特定の要素を取得する
```JS
const divs = document.querySelectorAll("div");
console.log(divs);
```
先ほどと同じように開発者ツールを開いて上のコードを実行してみてください.  
`div`要素の配列が表示されると思います.  
もしくは
```JS
console.log(divs[0]);
```
で `divs`の一番最初の要素を取得できます.
### 新しく要素を作る
`first.html`をブラウザで開き`Console`に以下をコピペしてください
```JS
const body = document.body; // body を定義
const newDiv = document.createElement("div"); // newDiv という名前の新しい div 要素を作る

newDiv.innerText = "This is newDiv"; // newDiv の中のテキストを設定
body.appendChild(newDiv); // body 一番最初の子要素を newDiv にする
```
`newDiv`が追加されているはずです.  

## 動き(?)
先ほどは基本的なJSの操作を学びましたね  
ではJSを使ってHTMLに動きをつけていきましょう!!
### `<script>`タグ
`first.html`の`<body>`の内側に以下の行を追加しましょう
```html
<script type="text/javascript">
    console.log("Hello!!");
</script>
```
ページを読み込み直すと、`Console`には`Hello`と表示されていると思います  
`<script>`タグはJSを書くときなどに使用します.
### `button`と関数
まずは`first.html`の`<body>`の内側に以下の行を追加しましょう
```html
<button onclick="clickEvent()">Click me</button>
```
次に`<script>`の内側に次のコードを追加しましょう
```js
function clickEvent() {
    console.log("clicked");
}
```
この状態で`Click me`ボタンを押すと`Console`には`clicked`と表示されるはずです

### `button`で要素を追加
やっと**動き**っぽいことをやります  
`<script>`タグ内に以下のコードを追加しましょう
```js
function clickEvent() {
        const body = document.body;
        const newDiv = document.createElement("div");

        newDiv.innerText = "This is newDiv";
        body.appendChild(newDiv);
}
```
`Click me`を押してみてください  
`This is newDiv`という文字列が画面に表示されたはずです.  
このようにJSを使うと画面上の文字を表示させることができます.


### 応用
次は応用例です. コピペして動作を確認してみましょう
```js
let i = 1;
const body = document.body;

function clickEvent() {
	if (i == 1) {
		createDiv();
		i *= -1;
	} else {
		eraseDiv();
		i *= -1;
	}
}

function createDiv() {
	const newDiv = document.createElement("div");
	newDiv.setAttribute("id", "new_div");
	newDiv.innerText = "This is newDiv"; 
	body.appendChild(newDiv); 			
}

function eraseDiv() {
	const newDiv = document.getElementById("new_div");
	newDiv.remove();
}
```

[目次に戻る](../README.md)