# 疑似要素のcontentを動的に変更する方法(Vue.js)

親から、子コンポーネントに`props`で`data`を渡す。


```vue
<template>
  <div class="home">
    <div class="hoge">
      <Item v-for="(post, i) in posts"
      :key="i" 
      v-bind:title="post.title" 
      v-bind:url="post.url" />
    </div>
  </div>
</template>

<script>
import Item from '@/components/Item'

export default {
  data() {
    return {
      posts: [
        {title: "タイトル1", url: "https://placehold.jp/500x150.png"},
        {title: "タイトル2", url: "https://placehold.jp/500x300.png"},
        {title: "タイトル3", url: "https://placehold.jp/500x400.png"},
        {title: "タイトル4", url: "https://placehold.jp/500x320.png"},
        {title: "タイトル5", url: "https://placehold.jp/500x300.png"},
        {title: "タイトル6", url: "https://placehold.jp/500x180.png"},
        {title: "タイトル7", url: "https://placehold.jp/500x320.png"},
        {title: "タイトル8", url: "https://placehold.jp/500x150.png"},
      ]
    }
  },
  components: {
    Item
  }
}  
</script>
```

子コンポーネントで受け取り`カスタム属性`でデータバインディング

```vue
<template>
    <div class="c-item">
        <a href="#" v-bind:data-title="title">
            <span style="font-size: 16px;">{{ title }}</span>
            <img :src="url" :alt="title">
        </a>
    </div>
</template>

<script>
    export default {
        name: "Item",
        props:[
            'title',
            'url'
        ]
    }
</script>

<style scoped lang="scss">
    .c-item a[data-title] {
        &::after {
            content: attr(data-title) "";
            text-align: center;
            font-size: 12px;
            font-weight: bold;
            color: #777;
        }
        &:hover::after {
            color: #fff;
        }
    }

    .c-item:hover:nth-child(1) a{
        background: #3b5998;
        &:before{background: #365492;}
        &:after{background: #4a69ad;}
    }
    .c-item:hover:nth-child(2) a{
        background: #00aced;
        &:before{background: #097aa5;}
        &:after{background: #53b9e0;}
    }
    .c-item:hover:nth-child(3) a{
        background: #dd4b39;
        &:before{background: #b33a2b;}
        &:after{background: #e66a5a;}
    }

    .c-item:hover:nth-child(4) a{
        background: #e4405f;
        &:before{background: #d81c3f;}
        &:after{background: #e46880;}
    }
</style>

```

ポイントはカスタム属性でデータバインディングし、cssの`attr()`関数で文字列を受け取る。