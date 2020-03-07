# Homebrewの引っ越し

## dump生成

```bash
$ brew bundle dump --global --force
```

上記コマンドで`.Brewfile`がユーザー直下に生成される。

## .Brewfileのインストール

生成した`.Brewfile`をinstallしたいMacのユーザー直下に保存し、以下のコマンドでインストールできる。

```bash
$ brew bundle --global
```
