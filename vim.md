# Vim設定メモ
極力Atomとか使いたいけど, ssh先でどうしてもエディタ使わざるを得ない場合があるので一応設定しておく.
未完成.

## 必要なもの
- Mac
    - vim

## やること
- setting

## setup vimrc

### files
ファイル周りの設定.
```
" バックアップを作らない
set nobackup
" スワップファイルを作らない
set noswapfile
```

### set number

```
" 行番号を表示する
set number
```

### cursorline
行番号のハイライト設定.
```
" カーソル行をハイライトするために必要
set cursorline
" _とかとかぶるのでcursorlineの色を消す
highlight clear CursorLine
" 行番号だけ色を変える, ctermbgで背景色, ctermfgで行番号の色をそれぞれ整数値で指定
highlight CursorLineNr ctermbg=255 ctermfg=0
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

### display hidden characters
不可視文字を表示する.
```
set list listchars=tab:>-,eol:↲,extends:»,precedes:«,nbsp:%
```
