# 演習05　Codespaces と VS Code で開発する

クラウド上に開発環境を作成し、設定をリポジトリに保存して再利用します。目安は1時間未満です。

## 始め方

1. 講師から案内された日本語版テンプレートの GitHub ページを開きます。**Use this template** → **Create a new repository** を選び、**Owner** と公開範囲を確認して **Create repository** を選びます。
2. 20秒ほど待って再読み込みします。自分のコピーの **Issues** または **README** に出る案内に合わせて、この資料の同じ番号を開きます。
3. ファイル名、ブランチ名、コード、指定コメントは掲載どおりに入力します。操作後は GitHub 上で次の案内を確認します。

[GitHub Skills の原文 README](https://github.com/skills/code-with-codespaces) · [教材のライセンス](LICENSE)

## Step 1　Codespace を起動して変更を送る

1. 自分のコピーで **Code** → **Codespaces** → **Create codespace on main** を選びます。ブラウザーの VS Code がつながるまで待ち、左下に接続先が表示されることを確認します。
2. **Explorer** で `src/hello.py` を開きます。**TERMINAL** で教材のコマンドを実行し、Node.js、Python、Ruby などのバージョン表示を控えます。
3. Python のサンプルを実行します。ファイルの中身を指定のコードに変更して保存し、コミットして GitHub にプッシュします。
4. 必要に応じて GitHub のファイルを開き、変更が反映されたことを確認します。

### 原文のコマンド・入力例

```bash
node --version
dotnet --version
python --version
gh --version
```

```bash
python src/hello.py
```

```py
print("Hello World!")
```

```bash
git add 'src/hello.py'
git commit -m 'fix: incomplete hello message'
git push
```

[このステップの原文](https://github.com/skills/code-with-codespaces/blob/main/.github/steps/1-first-codespace.md)

## Step 2　開発環境のイメージを指定する

イメージは開発環境の土台です。リポジトリの `.devcontainer/devcontainer.json` で指定すると、メンバーが同じ環境を作れます。

1. Codespace 内で `.devcontainer/devcontainer.json` を作り、指定の基本イメージを設定します。
2. 設定変更の通知を承認するか、コマンドパレットの `Codespaces: Rebuild Container` から **Rebuild** を選びます。
3. 再接続したら、ターミナルでバージョンを確認します。最初の環境にあったツールとの違いを見比べます。
4. Git LFS フックに関する原文の操作は、この演習用 Codespace 内で行います。設定をコミットし、教材の案内に従って GitHub に反映します。

### 原文のコマンド・入力例

```txt
.devcontainer/devcontainer.json
```

```bash
mkdir -p .devcontainer
touch .devcontainer/devcontainer.json
```

```json
{
  "name": "Basic Dev Environment",
  "image": "mcr.microsoft.com/devcontainers/base:debian"
}
```

```bash
node --version
dotnet --version
python --version
gh --version
```

```bash
rm .git/hooks/post-checkout
rm .git/hooks/post-commit
rm .git/hooks/post-merge
rm .git/hooks/pre-push
```

```bash
git add '.devcontainer/devcontainer.json'
git commit -m 'feat: Add codespace configuration'
git push
```

[このステップの原文](https://github.com/skills/code-with-codespaces/blob/main/.github/steps/2-custom-image.md)

## Step 3　Python、拡張機能、初期化スクリプトを追加する

1. コマンドパレットから `Codespaces: Add Dev Container Configuration Files...` → **Modify your active configuration...** を選びます。
2. `devcontainers` の **Python** → **Configure Options** を選び、**Install Tools** を `true`、バージョンを `3.10` にします。設定の `features` を確認します。
3. **Extensions** で **Python** と **Python Debugger** を探し、各項目を右クリックして **Add to devcontainer.json** を選びます。設定の `customizations` を確認します。
4. `.devcontainer/postCreate.sh` を作り、実行権限を付けます。指定のスクリプトを入れ、JSON の最上位に `postCreateCommand` を追加します。
5. 設定をコミットして GitHub に反映します。確認する場合は再構築し、拡張機能が有効か、Python のデバッグとターミナルの `sl` が動くか試します。

### 原文のコマンド・入力例

```txt
Codespaces: Add Dev Container Configuration Files...
```

```json
"features": {
   "ghcr.io/devcontainers/features/python:1": {
      "installTools": true,
      "version": "3.10"
   }
},
```

```json
"customizations": {
   "vscode": {
      "extensions": [
         "ms-python.python",
         "ms-python.debugpy"
      ]
   }
},
```

```txt
.devcontainer/postCreate.sh
```

```bash
touch .devcontainer/postCreate.sh
```

```bash
chmod +x .devcontainer/postCreate.sh
```

```bash
#!/bin/bash

sudo apt-get update
sudo apt-get install sl
echo "export PATH=\$PATH:/usr/games" >> ~/.bashrc
echo "export PATH=\$PATH:/usr/games" >> ~/.zshrc
```

```json
"postCreateCommand": ".devcontainer/postCreate.sh"
```

```shell
git add '.devcontainer/devcontainer.json'
git add '.devcontainer/postCreate.sh'
git commit -m 'feat: Add features, extensions, and postCreate script'
git push
```

```bash
node --version
dotnet --version
python --version
gh --version
```

```bash
sl
```

[このステップの原文](https://github.com/skills/code-with-codespaces/blob/main/.github/steps/3-customize-codespace.md)

## Step 4　Codespace を作り直して試す

1. 変更をプッシュ済みであることを確認し、VS Code のタブを閉じます。
2. 演習リポジトリで **Code** → **Codespaces** を開き、使用中の環境の `...` から **Delete** を選びます。
3. `+` または **Create codespace on main** で環境を作り直します。必要なら直前の操作を試し、設定が反映されていることを確認します。
4. 演習 Issue に下の指定コメントを投稿し、完了案内を待ちます。

### 原文のコマンド・入力例

```md
Hey @professortocat, I've finished testing out my new Codespace.
I'm ready to review!
```

[このステップの原文](https://github.com/skills/code-with-codespaces/blob/main/.github/steps/4-use-codespace.md)

## 振り返り

Codespace を作成し、コード変更をプッシュしました。イメージ、Python、拡張機能、初期化スクリプトを設定し、作り直した環境に引き継げることを確認しました。

[このステップの原文](https://github.com/skills/code-with-codespaces/blob/main/.github/steps/x-review.md)
