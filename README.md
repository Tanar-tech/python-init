# python-init

環境構築のためのプロジェクトです。

## 前提

OS：Windows（WSL2 Ubuntu）

## 構成

・バージョン管理
pyenv

・パッケージ管理
poetry

## Pyenv

1. Install

```sh
anyenv install pyenv
```

2. Python install

```sh
pyenv install 3.9.13
# ⇒　Build errorが表示された場合、パッケージ不足。
# ⇒　下記を実行
# sudo apt-get install make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
pyenv local 3.9.13
```

## Poetry

1. Install

```
$ curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python3
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
```

2. Config

```sh
poetry config virtualenvs.in-project true # VSCode用の設定。プロジェクトフォルダをVSCodeが認識できるようになる。
```

3. Project Initialize

```sh
poetry init # pyproject.tomlが作成される
poetry install # モジュールがインストールされる。
```

4. Tips

```sh
# ライブラリ追加
poetry add django
# 開発用ライブラリ追加
poetry add -D <name>
# requirements.txtエクスポート
poetry export -o requirements.txt
```
