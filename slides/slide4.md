## **【 3 】<br>Nuxtでの利用**

>>>

### パッケージのインストール
<hr>

```js
npm i gsap
```

>>>

### ページで各コンポーネントの<br>アニメーションを利用する
<hr>

1. コンポーネントにアニメーションの timeline を返すメソッドを作成
1. ページで timeline.add() を利用して各コンポーネントのアニメーションを組み合わせる

>>>

#### **コンポーネント内の記述**

```vue
<template>
  <div ref="sample">
    <!-- 内容 -->
  </div>
</template>

<script>
import gsap from 'gsap';
export default {
  methods: {
    sampleAnim() {
      const tl = gsap.timeline();
      tl.to(this.$refs.sample, {
        // アニメーション
      });
      return tl;
    }
  }
}
</script>
```

>>>

#### **ページ内の記述**

```vue
<template>
  <div>
    <Sample1 ref="sample1"></Sample1>
    <Sample2 ref="sample2"></Sample2>
    <button @click="pageAnim">実行ボタン</button>
  </div>
</template>

<script>
import gsap from 'gsap';
import Sample1 from '~/components/Sample1.vue';
import Sample2 from '~/components/Sample2.vue';

export default {
  methods: {
    pageAnim() {
      const tl = gsap.timeline();
      tl.add(this.$refs.sample1.sampleAnim1())
      .add(this.$refs.sample2.sampleAnim2(), '-=0.5');
    }
  }
}
</script>
```

>>>

### 一度だけアニメーションを<br>実行する
<hr>

1. store にアニメーション実行のフラグを作成
1. onComplete を利用して対象のアニメーション完了後にフラグを変更する

>>>

#### **storeの記述**

```js
export const state = () => ({
  opening: true,
})

export const mutations = {
  openingDone(state) {
    state.opening = false;
  }
}
```

>>>

#### **アニメーションの記述**

```vue
<script>
import gsap from 'gsap';

export default {
  methods: {
    openingAnim() {
      if(!this.$store.state.opening) return;
      const tl = gsap.timeline({
        onComplete: () => {
          this.$store.commit('openingDone');
        }
      });
      tl.add(this.Anim1())
      .add(this.Anim2());
    },
    Anim1() {...},
    Anim2() {...},
  }
}
</script>
```
