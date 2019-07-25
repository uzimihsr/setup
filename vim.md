# Vim設定メモ
極力Atomとか使いたいけど, ssh先でどうしてもエディタ使わざるを得ない場合があるので一応設定しておく.
未完成.

## 必要なもの
- Mac
    - vim

## やること
- [setup .vimrc](#setup-.vimrc)
- [install iceberg](#install-iceberg)

## setup .vimrc

### settings
ほぼおまじない
```
set encoding=utf-8
scriptencoding utf-8
" vi互換を切る(本当はいらないらしい)
set nocompatible
" バックアップを作らない
set nobackup
" スワップファイルを作らない
set noswapfile
```

### tab
`tab`まわりの設定.
```
" tabをspaceに変換
set expandtab
" tabの幅
set tabstop=4
" tabを押したときに挿入されるspaceの数
set softtabstop=4
" インデントで挿入されるtabの長さ
set shiftwidth=4
" 自動インデントを有効にする
set autoindent
```

### display
表示まわりの設定

```
" タイトルを表示
set title
" コマンドを表示
set showcmd
" カーソル位置を表示
set ruler
" 背景を暗くする
"set background=dark
" ステータス行を表示させる
set laststatus=2
" シンタックスを効かせる
syntax enable
" 長過ぎる行を折り返す
set wrap
" 不可視文字を表示する
set list listchars=tab:>-,eol:↲,extends:»,precedes:«,nbsp:%
" 行番号を表示する
set number
" カーソル行をハイライトするために必要
set cursorline
" _とかとかぶるのでcursorlineの色を消す
highlight clear CursorLine
" 行番号の色を固定する(カラースキームの前に設定)
autocmd ColorScheme * highlight LineNr ctermfg=255
" カラースキーム
colorscheme iceberg
" 行番号だけ色を変える, ctermbgで背景色, ctermfgで行番号の色をそれぞれ整数値で指定
highlight CursorLineNr ctermbg=255 ctermfg=0
" マウスを有効にする
set mouse=a
```

# search
検索周りの設定

```
" 大文字小文字を区別しない
set ignorecase
" 検索語句に大文字が含まれる場合はignorecaseを無効化する
set smartcase
" 検索結果をハイライトする
set hlsearch
" インクリメンタルサーチ
set incsearch
" 検索結果が一番下まで行ったら一番上に戻る
set wrapscan
```

## install iceberg
[iceberg](https://cocopon.github.io/iceberg.vim/)を入れる.

```
$ mkdir ~/.vim/colors
$ cd ~/.vim/colors
$ curl -O https://raw.githubusercontent.com/cocopon/iceberg.vim/master/colors/iceberg.vim
```

`.vimrc`に追記
```
colorscheme iceberg
```
