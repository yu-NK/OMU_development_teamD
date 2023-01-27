# 先端ソフトウェア環境構築実践 チームD
新しく設立された大阪公立大学の情報学研究科を紹介するWebページ用のソースコード．ここでは，情報学研究科の学生（チームDの6名）が実際に行っている研究を簡単に紹介している．

## docker環境の内容
ローカルのブラウザでWebページを表示するための簡易的な環境構築である．

Dockerfileからdockerイメージをビルドする際にGithubのレポジトリからクローンし、ApacheのWebコンテンツ保存ディレクトリに格納する．その後は，dockerコンテナを起動する度に`git pull`を実行し，最新の状態に更新する．

ベースとなるdockerイメージ：`httpd:latest`

## 環境構築の方法
ここではdockerとdocker-composeが使える環境であることを想定して説明する．環境構築の方法は以下の3つの方法でできる．
### docker-composeを使う場合

1. レポジトリのクローン
```shell
# git clone https://github.com/yu-NK/OMU_development_teamD.git
もしくは
# git clone git@github.com:yu-NK/OMU_development_teamD.git
```

2. Dockerfileとdocker-compose.ymlがあるディレクトリに移動
```shell
# cd OMU_development_teamD/docker
``` 
3. コンテナの起動
```shell
# docker-compose up -d
```
### docker Hubからイメージをダウンロードする場合
1. docker Hubからイメージをダウンロード
```shell
# docker pull yunk106/omu_develop_teamd_image:latest
```

2. ダウンロードしたイメージから，dockerコンテナを起動
```shell
# docker run -d -p 9000:80 yunk106/omu_develop_teamd_image:latest
```

#### イメージの格納場所（docker Hub）
https://hub.docker.com/r/yunk106/omu_develop_teamd_image

### Dockerfileを用いる場合

1. Dockerfileが保存されているディレクトリでビルド
```shell
# docker build -t omu_develop_teamd_image .
```

2. 作成したイメージをもとに、dockerコンテナを起動
```shell
# docker run -d -p 9000:80 omu_develop_teamd_image
```

## Webページにアクセスする方法
dockerコンテナが起動後，http://localhost:9000 にアクセスすることで，Webページが表示される．
