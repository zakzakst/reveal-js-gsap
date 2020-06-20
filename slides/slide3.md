## **【 2 】<br>スクリプトの記述方法**

>>>

### ライブラリの読み込み
<hr>

https://greensock.com/docs/v3/Installation
<small>※他のライブラリへの依存はなし</small>

- ファイルダウンロード
- CDN
- npmパッケージ

>>>

### アニメーションさせる
<span style="color: #e7ad52">（ to、from、fromTo ）</span>
<hr>

<iframe height="265" style="width: 100%;" scrolling="no" title="GSAP Basic Tween" src="https://codepen.io/GreenSock/embed/wvwEOZL?height=265&theme-id=dark&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/GreenSock/pen/wvwEOZL'>GSAP Basic Tween</a> by GreenSock
  (<a href='https://codepen.io/GreenSock'>@GreenSock</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

>>>

```js
gsap.to('.box', {
  rotation: 27, // 27度回転
  x: 100, // 100px水平移動
  duration: 1, // 1秒かけてアニメーション
});

gsap.to() // 変化後の状態を指定
gsap.from() // 変化前の状態を指定
gsap.fromTo() // 変化前後の状態を指定（第二引数：変化前、第三引数：変化後）
```

- 第一引数でアニメーションさせる要素を指定
- 第二引数で変化前後の状態を指定

>>>

```js
const element1 = document.getElementById('id-1');
const element2 = document.getElementById('id-2');

gsap.to(element1, {...});
gsap.to([element1, element2], {...});
```

- DOMでの要素指定も可能
- 配列形式で複数要素を指定できる

>>>

#### **その他**

- 複数要素を連続してアニメーションさせる<br>https://greensock.com/docs/v3/Staggers

- 変化を配列や関数で指定する<br>https://codepen.io/GreenSock/pen/oNveWzg

- 状態を設定、クリアする<br>https://greensock.com/docs/v3/GSAP/gsap.set()

- イージングが豊富<br>https://greensock.com/docs/v3/Eases

>>>

### アニメーションをつなげる
<span style="color: #e7ad52">（ timeline ）</span>
<hr>

<iframe height="265" style="width: 100%;" scrolling="no" title="GSAP Starter Pen" src="https://codepen.io/GreenSock/embed/OJPaGbz?height=265&theme-id=dark&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/GreenSock/pen/OJPaGbz'>GSAP Starter Pen</a> by GreenSock
  (<a href='https://codepen.io/GreenSock'>@GreenSock</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

>>>

```js
const tl = gsap.timeline();

tl.to('.box1', {...})
.to('.box2', {...}) // 前のアニメーションが終了したらスタート
.to('.box3', {...}, '-=1') // 前のアニメーション終了の1秒前からスタート
.to('.box4', {...}, '+=1'); // 前のアニメーション終了の1秒後からスタート
```

- timelineに各アニメーションをつなげていく
- 第三引数にはアニメーションの開始位置を指定

>>>

#### **その他**

- アニメーションを繰り返す<br>https://codepen.io/GreenSock/pen/OJPaGbz

- 個別に設定したアニメーションを組み合わせる<br>https://codepen.io/GreenSock/pen/rNVNpVE

- 再生をコントロールする<br>https://codepen.io/talia_longname/pen/qrEKbO
