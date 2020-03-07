# jenvの使い方
※要anyenvインストール

## 手順

1. anyenv使用してjenvをインストール

```bash
$ anyenv install jenv
```

2. JDKの最新版をインストール

```bash
$ brew install java
```

3. インストール済みのJDK確認方法

```bash
$ /usr/libexec/java_home -V
Matching Java Virtual Machines (1):
    12.0.1, x86_64:	"OpenJDK 12.0.1"	/Library/Java/JavaVirtualMachines/openjdk-12.0.1.jdk/Contents/Home
```

4. jenvで管理するJDKのバージョンを指定する

```bash
$ jenv add /Library/Java/JavaVirtualMachines/openjdk-12.0.1.jdk/Contents/Home
```

5. グローバルのバージョンを指定

```bash
$ jenv global 12.0.1
```

6. 確認

```bash
$ jenv versions
  system
  12.0
* 12.0.1
  openjdk64-12.0.1
```
