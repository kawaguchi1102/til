# vueファイルで共通のCSSを読み込む

`Vue Cli 3`の`vue create`コマンドで作成したプロジェクトには、`webpack.config`がないので、プロジェクト直下に`vue.config.js`というファイルを作成する。
`vue.config.js`に以下を記載することで、`assets/scss`以下の`app.scss`を読み込むことができる。


```:vue.config.js
module.exports = {  
  css: {
    loaderOptions: {
      sass: {
        data: `@import "@/assets/scss/app.scss";`
      }
    }
  }
}
```

