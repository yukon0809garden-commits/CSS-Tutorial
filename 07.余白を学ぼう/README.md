余白を学ぶことで要素同士の間隔や、要素の境界を設定できるようになります。余白や境界を設定するプロパティは主に`margin`、`border`、`padding`の 3 つがあり、それぞれが指すエリアは以下の通りです。

![image](https://github.com/user-attachments/assets/8424b152-fc05-45aa-a46c-c0c298f6307a)

## border

`border`プロパティは要素の境界を設定します。要素を四角で囲うとイメージがしやすくなるので以下の例を見てみましょう。

```html
<p>Python</p>
<p>JavaScript</p>
```

```css
p {
  display: inline-block;
  width: 100px;
  background-color: #3776ab;
  color: white;
  text-align: center;
}
```

![image](https://github.com/user-attachments/assets/f1fdd6ea-b3e3-4439-927e-7f39a01c42b1)

2 つの`p`要素に`border`プロパティを追加してみます。

```css
p {
  display: inline-block;
  width: 100px;
  background-color: #3776ab;
  color: white;
  text-align: center;
  /* borderプロパティを追加 */
  border: 2px solid red;
}
```

![image](https://github.com/user-attachments/assets/75f144dd-a536-4b8c-9957-32603693990f)

今は`padding`プロパティを指定していないため、要素エリアのすぐ外側に 2px の`border`エリアが表示されました。

値には、色、線の太さ、線の種類を指定します。線の種類は、今回は実線（`solid`）としていますが、他にも点線（`dotted`）や破線（`dashed`）などがあります。

![image](https://github.com/user-attachments/assets/802c5c05-ff20-41aa-88f8-4604cf422457)

![image](https://github.com/user-attachments/assets/7f2593c4-7b43-48fc-a2de-97feee97057d)

## padding

`padding`プロパティは要素と`border`エリアの間になります。先ほどの例に`padding`プロパティを追加してみましょう。

```css
p {
  display: inline-block;
  width: 100px;
  background-color: #3776ab;
  color: white;
  text-align: center;
  border: 2px solid red;
  /* paddingプロパティを追加 */
  padding: 10px;
}
```

![image](https://github.com/user-attachments/assets/fa384885-ad82-4e9c-b312-df3f7aa607cf)

見た目ではボタンのサイズが大きくなったように感じますが、実際には文字のまわりに余白（padding）が 10px ぶん追加されただけです。上下に同じ余白をつけたことで、文字が上下の中央にきれいに配置されるようになりました。

これは、height（高さ）を自分で指定していない場合、文字の大きさに合わせて自動で高さが決まるため、上下の余白だけを指定すれば、自然に文字が真ん中に見えるようになるからです。

## margin

`margin`プロパティは`border`エリアの外側のエリアになります。先ほどの例に`margin`プロパティを追加してみましょう。

```css
p {
  display: inline-block;
  width: 100px;
  background-color: #3776ab;
  color: white;
  text-align: center;
  border: 2px solid red;
  padding: 10px;
  /* marginプロパティを追加 */
  margin: 50px;
}
```

![image](https://github.com/user-attachments/assets/a9fba72f-b013-4da7-96db-d2175843a6a7)

要素間の間隔や画面内での位置が変わりましたね。これは各`p`要素に`margin`プロパティが設定されたためです。

## 上下左右のそれぞれへの指定

紹介した 3 つのうち`padding`と`margin`プロパティでは、上下左右それぞれに個別に値を設定することができます。設定方法は以下の通りです。

- 値が 1 つ：上下左右すべてに指定した値を適用（`padding: 10px;`）
- スペース区切りで値が 2 つ：前側の値が上下に、後側の値が左右に適用（`padding: 5px 1px;`）
- スペース区切りで値が 3 つ：前側の値が上に、中央の値が左右に、後側の値が下に適用（`padding: 5px 1px 5px;`）
- スペース区切りで値が 4 つ：前の値から上、右、下、左に適用（`padding: 1px 5px 1px 5px;`）

また、それぞれを指定するためのプロパティも存在します。

- `padding-top`、`margin-top`：上
- `padding-right`、`margin-right`：右
- `padding-bottom`、`margin-bottom`：下
- `padding-left`、`margin-left`：左

`border`プロパティは 3 種類の値が存在するため、それぞれ個別に指定するためのプロパティを使用することで、`padding`プロパティや`margin`プロパティと同様に上下左右を個別に指定することができます。

- 色：`border-color`
- 線の太さ：`border-width`
- 線の種類：`border-style`

そして、こちらにも各プロパティに`-top`や`-right`を追加したプロパティ（`border-top-color`や`border-right-style`）が存在するため、それぞれを単体で指定することが可能です。

## outline

`outline`プロパティは、`border`プロパティと同じように「枠線」を追加するためのプロパティです。見た目の指定方法（色・線の太さ・線の種類）は似ていますが、いくつか**重要な違い**があります。

---

### `border`と`outline`の違い

| 項目               | `border`                       | `outline`                            |
| ------------------ | ------------------------------ | ------------------------------------ |
| 上下左右の個別指定 | 可能（`border-top`など）       | 不可（全体のみ）                     |
| 枠線の位置         | 要素の**内側**                 | 要素の**外側**                       |
| サイズへの影響     | 枠線の太さで**サイズが変わる** | **サイズは変わらない**               |
| レイアウトの影響   | あり                           | なし                                 |
| 主な使いどころ     | 常時表示される枠               | 一時的な強調（例：`hover`, `focus`） |

---

以下は`border`と`outline`の違いです。

```html
<div class="box">
  <div class="border"></div>
  <p>Python</p>
</div>
<div class="box">
  <div class="outline"></div>
  <p>JavaScript</p>
</div>
```

```css
p {
  margin: 0 0 20px 0;
  text-align: center;
}

.box {
  display: inline-block;
  margin: 20px;
  background-color: aqua;
}

.border,
.outline {
  display: inline-block;
  width: 100px;
  padding: 20px 0;
  background-color: #3776ab;
}

/* borderクラスにborderプロパティで枠線を追加 */
.border {
  border: red 5px solid;
}

/* outlineクラスにoutlineプロパティで枠線を追加 */
.outline {
  outline: red 5px solid;
}
```

![image](https://github.com/user-attachments/assets/a4575630-f2a0-4848-8fb3-34b626b3cc76)

この例では、Python と JavaScript のボックスは**まったく同じスタイル**ですが、追加している枠線のプロパティが異なります。

- `border`を使った **Python 側** では、枠線が水色のエリア（`.box`）の**内側**に描かれています。  
  `border`の太さ（5px）の分だけ、要素のサイズが大きくなり、`.box`の大きさにも影響しています。

- `outline`を使った **JavaScript 側** では、枠線が水色のエリアの**外側**に描かれています。  
  `outline`は**要素のサイズを変えずに枠線だけを表示できる**ため、`.box`のサイズや配置に影響しません。

## CSS を書いてみよう

インプットした内容を基に、早速手を動かして試してみましょう。index.html を確認し、指示に従って CSS を書いてください。まずは自身で書いてみて、わからなければ回答例を見ても OK です。index.html をブラウザで表示して、ビフォーアフターも確認してみてください。

index.html

```html
<!DOCTYPE html>
<html lang="ja">
  <head>
    <meta charset="UTF-8" />
    <link
      rel="stylesheet"
      href="styles.css" />
    <title>Document</title>
  </head>
  <body>
    <h1>CSSハンズオン</h1>
    <h3>Part7</h3>
    <p>ダッシュボード</p>
    <p>講義動画</p>
    <p>講義日程</p>
    <p>ステップ一覧</p>
    <p>ハッカソン</p>
  </body>
</html>
```

1. すべての`p`要素をサイズを変更できるインラインブロックにしてください。
   <details>
   <summary>回答例</summary>

   ```css
   /* p要素に適用するスタイル */
   p {
     display: inline-block;
   }
   ```

   </details>

2. すべての`p`要素の背景色を`#00008B`、文字色を白色にしてください。
   <details>
   <summary>回答例</summary>

   ```css
   /* p要素に適用するスタイル */
   p {
     display: inline-block;
     background-color: #00008b;
     color: white;
   }
   ```

   </details>

3. すべての`p`要素の幅を 160px にし、各要素の文字が左右方向で中央になるようにしてください。

   ![image](https://github.com/user-attachments/assets/f66648be-c067-4eff-97f3-28c43af62e1e)

   <details>
   <summary>回答例</summary>

   ```css
   /* p要素に適用するスタイル */
   p {
     display: inline-block;
     background-color: #00008b;
     color: white;
     width: 160px;
     text-align: center;
   }
   ```

   </details>

4. すべての`p`要素に`padding`を上下にのみ 10px ずつ追加してください。
   <details>
   <summary>回答例</summary>

   ```css
   /* p要素に適用するスタイル */
   p {
     display: inline-block;
     background-color: #00008b;
     color: white;
     width: 160px;
     text-align: center;
     padding: 10px 0;
   }
   ```

   </details>

5. すべての`p`要素に`margin`を右にだけ 20px 追加してください。
   <details>
   <summary>回答例</summary>

   ```css
   /* p要素に適用するスタイル */
   p {
     display: inline-block;
     background-color: #00008b;
     color: white;
     width: 160px;
     text-align: center;
     padding: 10px 0;
     margin-right: 20px;
   }
   ```

   </details>

6. すべての`p`要素に以下の内容で`border`を適用してください。

   |     | 色   | 線の太さ | 線の種類 |
   | --- | ---- | -------- | -------- |
   | 上  | 黄色 | 5px      | 点線     |
   | 右  | 黄色 | 10px     | `ridge`  |
   | 下  | 赤色 | 10px     | `ridge`  |
   | 左  | 黄色 | 5px      | 実線     |

   <details>
   <summary>回答例</summary>

   ```css
   /* p要素に適用するスタイル */
   p {
     display: inline-block;
     background-color: #00008b;
     color: white;
     width: 160px;
     text-align: center;
     padding: 10px 0;
     margin-right: 20px;
     border-style: dotted ridge ridge solid;
     border-color: yellow yellow red yellow;
     border-width: 5px 10px 10px 5px;
   }
   ```

   </details>

すべて記述できるとブラウザでは以下のように表示されます。うまく表示されない場合は、コードを良く見返して修正しましょう。

![image](https://github.com/user-attachments/assets/4b34b86c-f56c-4b0c-b44e-ea666cde425d)

## GitHub へプッシュしよう

編集した内容をステージング＆コミットし、自身の GitHub にあるリモートリポジトリにプッシュしましょう。以下のコマンドを実行します。

```bash
# すべてのファイルをステージング
git add .

# コミット（コミットメッセージは自由に記述してください）
git commit -m "Part7 余白を学ぼう"

# リモートリポジトリへプッシュ
git push origin main
```
