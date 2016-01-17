GoeGigを使ってみる

#GeoGigをローカル環境にインストールしてみる
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


#GeoGigを仮想環境で動かしてみる

##GgeGigのVirtualBoxのファイルのダウンロード
・VirtualBox
https://www.virtualbox.org/wiki/Downloads
・GeoGig virtual machine
http://training-files.boundlessgeo.com/foss4g/geogig-vm.ova

※参考資料
https://2015.foss4g-na.org/sites/default/files/slides/


##GeoGigのコマンドを確かめる

```
> geogig --help

The most commonly used geogig commands are:
--help          Print this help message, or provide a command name to get help for
--version       Display GeoGig version information
add             Add features to the staging area
apply           Apply a patch to the current working tree
blame           Shows information about authors of modifications for a single feature
branch          List, create, or delete branches
checkout        Checkout a branch or paths to the working tree
cherry-pick     Apply the changes introduced by existing commits
clean           Deletes untracked features from working tree
clone           Clone a repository into a new directory
commit          Record staged changes to the repository
config          Get and set repository or global options
conflicts       Shows existing conflicts
diff            Show changes between commits, commit and working tree, etc
fetch           Download objects and refs from another repository
format-patch    Creates a patch with a set of changes
geojson         GeoGig/GeoJSON integration utilities
help            Print this help message, or provide a command name to get help for
init            Create an empty geogig repository or reinitialize an existing one
log             Show commit logs
ls              Obtain information about features in the index and the working tree.
merge           Merge two or more histories into one
oracle          GeoGig/Oracle integration utilities
osm             GeoGig/OpenStreetMap integration utilities
pg              GeoGig/PostGIS integration utilities
pull            Fetch from and merge with another repository or a local branch
push            Update remote refs along with associated objects
rebase          Forward-port local commits to the updated upstream head
remote          remote utilities
reset           Reset current HEAD to the specified state, optionally modifying index and working tree to match
revert          Revert commits to undo the changes made
rm              Remove features or trees
serve           Serves a repository through the web api
show            Displays information about a commit, feature or feature type
shp             GeoGig/Shapefile integration utilities
sl              GeoGig/SpatiaLite integration utilities
sqlserver       GeoGig/SQL Server integration utilities
squash          Squash commits
status          Show the working tree status
tag             creates/deletes tags
version         Display GeoGig version information
```

##GeoGigの初期設定

GeoGigで利用する名前とメールアドレスを設定する。名前は英字で入力する。

```名前とメールアドレスを設定する
> geogig config --global user.name "Author"
> geogig config --global user.mail "author@example.com"
```
※""は入れない。

```コマンド出力を読みやすくする
> geogig config --global color.ui auto
```

~/.geogigconfigを確認する

```
>vi ~/.geogigconfig

[user]
name = Author
email = author@example.com
[color]
ui = auto
```

##GeoGigの基本操作

###geogig init
GeoGigでバージョン管理を始めるには、リポジトリの初期化をしなかればならない。GeoGigではgeogig initコマンドを利用して初期化を行い「.geogig」ファイルを作成する。

```リポジトリを初期化
> cd Desktop
> mkdir hogehoge
> cd hogehoge
> geogig init
```

###geogig status

```リポジトリの状態を確認
> geogig status

# On branch master
nothing to commit (working directory clean)
```

###geogig shp import

```shpファイルのデータインポート
> geogig shp import ../sample_data/snapshot1/parks.shp

Importing from shapefile ../sample_data/snapshot1/parks.shp

Importing parks            (1/1)...
33%
3 distinct features inserted in 82.33 ms

Building final tree...

3 features tree built in 2.639 ms
100%
snapshot1/parks.shp imported successfully.
```

```importのリポジトリの状態を確認
> geogig status

# On branch master
# Changes not staged for commit:
#   (use "geogig add <path/to/fid>..." to update what will be committed
#   (use "geogig checkout -- <path/to/fid>..." to discard changes in working directory
#
#      added  parks
#      added  parks/3
#      added  parks/2
#      added  parks/1
#4 total.

```


```shpファイルのデータインポートのエラーの場合
> geogig shp import /hoge/snapshot1/parks.shp

The shapefile '/hoge/snapshot1/parks.shp' could not be found, skipping...
```






