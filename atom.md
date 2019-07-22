# Atom設定メモ

## 必要なもの
- Mac
    - 特になし
- Linux
    - 特になし

## やること
- [install Atom](#install-Atom)
- [install file-icons](#install-file-icons)
- [install script](#install-script)
- install atom-ide-ui
- install ide-python
- install atom-beautify

## install Atom

### Macの場合
[Atom](https://atom.io/)をダウンロード. 展開した`Atom.app`を`/Applications/`に配置.

GitHub連携とかはやらなくてもいい, Gitタブだけでもかなり便利.

## install file-icons
[file-icons](https://atom.io/packages/file-icons)

各ファイルのアイコンをかわいくしてくれる.

```
$ apm install file-icons
```

または

`Preferences -> Install -> Packages`で`file-icons`を検索. いっぱい出てくるけど画像のものをInstall.

![file-icons](images/atom-file-icons.png)

## install script
[script](https://atom.io/packages/script)

Atom上でファイルを実行してくれる.

```
$ apm install script
```

`Preferences -> Install -> Packages`で`script`を検索. たぶん一番上にくるやつをInstall.

![script](images/atom-script.png)

実行したいファイルを開いた状態で`⌘I`を押すと実行される.

内部的にはファイルの拡張子から推測した実行コマンド(.pyなら`python`)を選んでいるっぽい. pythonの仮想環境を有効にするのはちょいめんどくさいかも

## install atom-beautify
[atom-beautify](https://atom.io/packages/atom-beautify)

コードを自動整形してくれる. 言語ごとに追加で必要なBeautifiersを入れる必要がある. 詳しくは公式を参照.

もしかしたらide-uiで十分かも

## install linter
文法エラーを指摘してくれる. 言語ごとに追加のPackageを入れる必要あり.

もしかしたらide-uiで十分かも
