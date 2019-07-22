# python環境構築メモ

## 必要なもの
- Mac
    - brew

## やること
- [install python](#install-python)
- [install pipenv](#install-pipenv)

## install python

Macの場合:

デフォルトでpythonとpython3が使えるはずなので特にすることなし.

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