# python環境構築メモ

## 必要なもの
- Mac
    - brew

## やること
- [install python](#install-python)
- [install pipenv](#install-pipenv)
- [install flake8](#install-flake8)

## install python

Macの場合:

デフォルトで`/usr/bin/python`にpython2系が入っているが, brewで入れ直す

```
$ brew install python@2
$ brew install python3
```

`/usr/local/bin/python`にpython2系が, `/usr/local/bin/python3`にpython3系がインストールされる.

## install pipenv

仮想環境の切り分けに[Pipenv](https://docs.pipenv.org/en/latest/)を使う.

```
$ brew install pipenv
```

プロジェクト内に環境を構築するよう環境変数`PIPENV_VENV_IN_PROJECT`を設定する. いちいち打つのは面倒なので.zshenvとかに書いておく.

```
$ export PIPENV_VENV_IN_PROJECT=1
```

仮想環境を分けるには対象のディレクトリで`pipenv --python [バージョン]`を打つ. すでに入ってるもの以外のが必要ならpyenvで入れられるらしい. 知らん.

```
$ pipenv --python 2.7
```

`Pipfile`と`.env`が作成されるはず. 仮想環境に入るときは`Pipfile`と`.env`があるディレクトリに移動して

```
$ pipenv shell
```

出るときは

```
$ exit
```

Atom用にpython3の環境を作っておく

```
$ mkdir ~/python-atom
$ cd ~/python-atom
$ pipenv --python 3.7
```

## install flake8
[flake8](https://pypi.org/project/flake8/)

文法チェックツール(linter).

```
$ cd ~/python-atom
$ pipenv shell
$ pipenv install flake8
```

`$ flake8 xxxx.py`でチェックしてくれる.

## install autopep8
[autopep8](https://pypi.org/project/autopep8/)

コード整形ツール(formatter). PEP8準拠.

```
$ cd ~/python-atom
$ pipenv shell
$ pipenv install autopep8
```

`$ autopep8 --in-place xxxx.py`で整形してくれる.

## install isort
[isort](https://github.com/timothycrosley/isort)

pythonのimport文を綺麗にしてくれる.

```
$ cd ~/python-atom
$ pipenv shell
$ pipenv install isort
```

`$ isort xxxx.py`でimport文のソートを実行してくれる.

## install language-server
[python-language-server](https://github.com/palantir/python-language-server)

pythonのLSP.

```
$ cd ~/python-atom
$ pipenv shell
$ pipenv install 'python-language-server[all]'
```
