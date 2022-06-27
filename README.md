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

```sh
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python3
# パスに追加。bashrcの場合。
echo 'export PATH="$HOME/.poetry/bin:$PATH"' >> ~/.bashrc
```

2. Config

```sh
# VSCode用の設定。プロジェクトフォルダをVSCodeが認識できるようになる。
poetry config virtualenvs.in-project true
```

3. Project Initialize

```sh
# pyproject.tomlが作成される
poetry init
# モジュールがインストールされる。
poetry install
```

4. Tips

```sh
# ライブラリ追加
poetry add django
# 開発用ライブラリ追加
poetry add -D django
# requirements.txtエクスポート
poetry export -o requirements.txt
```

## Formatter

Black を利用。

```sh
poetry add -D black
poetry add -D isort
```

pyproject.toml に設定追加
※行の最大文字数が 88 と若干尾の足りないので、120 に変更

```
[tool.black]
line-length = 120
[tool.isort]
profile = "black"
```

## Linter

flake8 を利用。

```sh
poetry add -D pyproject-flake8
```

pyproject.toml に設定追加
※Formatter に合わせて行の最大文字数を変更
※.venv のチェックを外す。

```
[tool.flake8]
max-line-length = 120
exclude = ".venv"
```

## VSCode の設定（Linter, Formatter 関連）

settings.json に下記を追加

```json
{
  "python.linting.enabled": true,
  "python.linting.pylintEnabled": false,
  "python.linting.flake8Enabled": true,
  "python.linting.lintOnSave": true,
  "python.formatting.provider": "black",
  "python.formatting.blackArgs": ["--line-length", "119"],
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.organizeImports": true
  }
}
```
