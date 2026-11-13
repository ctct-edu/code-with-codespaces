## Step 3　Python、拡張機能、初期化スクリプトを追加する

1. コマンドパレットから `Codespaces: Add Dev Container Configuration Files...` → **Modify your active configuration...** を選びます。
2. `devcontainers` の **Python** → **Configure Options** を選び、**Install Tools** を `true`、バージョンを `3.10` にします。設定の `features` を確認します。
3. **Extensions** で **Python** と **Python Debugger** を探し、各項目を右クリックして **Add to devcontainer.json** を選びます。設定の `customizations` を確認します。
4. `.devcontainer/postCreate.sh` を作り、実行権限を付けます。指定のスクリプトを入れ、JSON の最上位に `postCreateCommand` を追加します。
5. `.devcontainer/devcontainer.json` と `.devcontainer/postCreate.sh` をコミットし、`git push` で GitHub に反映します。確認する場合は再構築し、拡張機能が有効か、Python のデバッグとターミナルの `sl` が動くか試します。

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

### 画面での確認

- 左端の四角が並ぶアイコンが **Extensions** です。上の検索欄から拡張機能を探し、結果の項目を右クリックします。
- 左の **Explorer** で `.devcontainer` を開き、`devcontainer.json` と `postCreate.sh` が同じ階層にあることを確認します。再構築を試す場合は、**Extensions** で2つの拡張機能が有効か確認します。

[原文](https://github.com/skills/code-with-codespaces/blob/main/.github/steps/3-customize-codespace.md)
