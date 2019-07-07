# GCEにGCSをマウントする方法

## SETUP
SSHを立ち上げ以下のコマンドを入力

```bash
$ export GCSFUSE_REPO=gcsfuse-`lsb_release -c -s`
$ echo "deb http://packages.cloud.google.com/apt $GCSFUSE_REPO main" | sudo tee /etc/apt/sources.list.d/gcsfuse.list
$ curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
$ sudo apt-get -y update
$ sudo apt-get -y install gcsfuse
```


ディレクトを作成しGCSをマウントさせる

```bash
$ cd /var/www/html/
$ sudo mkdir {リソースのディレクト名}
$ sudo gcsfuse -o allow_other -o nonempty {GCSで作成したバケット名} /var/www/html/{マウントするディレクト}
```

---

## 備考

GCEインスタンスを停止し再度稼働させるとGCSのマウントが外れることがある。
対策として、GCEインスタンス起動時にシェルを実行する。

### GCEインスタンス起動時シェル実行の設定方法

VM インスタンスの詳細>編集>カスタム メタデータ

#### キー

startup-script

#### 値

```bash
#! /bin/bash
sudo gcsfuse -o allow_other -o nonempty {GCSバケット名} /var/www/html/{マウントするディレクト}
```

