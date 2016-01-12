# GeoGig
GoeGigを使ってみる
##インストール
①JDK7をインストール
http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html

②Homebrewからmevenのインストール

```Homebrewからmeveをインストール
brew install maven
```

```mavenのバージョンの確認
mvn --v
```
http://qiita.com/yamakz/items/8f48cd5c6806caf97e45
http://maven.apache.org/download.cgi


③GitHubからGeoGigをClone

```GeoGigをクローン
git clone http://github.com/boundlessgeo/GeoGig.git
```

③GeoGigのインストール
クローンしたGeoGigファイル内の src/parent に移動してインストール

```GeoGigのインストール
cd GeoGig/src/oarent
mvn clean install
geogig --help
```

↑失敗

