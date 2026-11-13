## Step 2　開発環境のイメージを指定する

イメージは開発環境の土台です。リポジトリの `.devcontainer/devcontainer.json` で指定すると、メンバーが同じ環境を作れます。

1. Codespace 内で `.devcontainer/devcontainer.json` を作り、指定の基本イメージを設定します。
2. 右下に設定変更の通知が出たら **Rebuild Now** を選びます。通知が見当たらなければ、コマンドパレットの `Codespaces: Rebuild Container` から **Rebuild** を選びます。
3. 再接続したら、ターミナルでバージョンを確認します。最初の環境にあったツールとの違いを見比べます。
4. Git LFS フックに関する原文の操作は、この演習用 Codespace 内で行います。下の例のとおり設定をコミットし、`git push` で GitHub に反映します。

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

### 画面での確認

- 左端の **Explorer** でリポジトリの最上位に `.devcontainer` フォルダを作り、その中に `devcontainer.json` を作ります。ファイル名の前のドットを含めて入力します。
- 再構築の通知が見当たらない場合は、VS Code 上部のコマンドパレットを `Ctrl+Shift+P`（Mac は `Cmd+Shift+P`）で開きます。再接続後は下部の **TERMINAL** でバージョンを確認します。

[原文](https://github.com/skills/code-with-codespaces/blob/main/.github/steps/2-custom-image.md)
