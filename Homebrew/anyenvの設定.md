# anyenvの設定

```bash
$ brew install anyenv
```

``` bash
$ echo 'eval "$(anyenv init -)"' >> ~/.bash_profile
$ exec $SHELL -l
```

## インストールできるenvの一覧

```bash
$ anyenv install -l
```

## pyenvのインストール

```bash
$ anyenv install pyenv
$ exec $SHELL -l
```

```bash
$ pyenv install 3.7.0
$ pyenv global 3.7.0
$ pyenv global
$ anyenv version
```
