# Nuxt.jsでdotenvを使用する方法


## 手順

1. @nuxtjs/dotenvをインストール

        $ yarn add @nuxtjs/dotenv

1. nuxt.config.jsにmodulesを追加する

        modules: [
          '@nuxtjs/dotenv'
        ],

1. プロジェクト直下に`.env`作成

        $ touch .env
    `.env`を編集する

        HOGE = hogehoge
    `process.env.HOGE`で`hogehoge`を参照することができる
