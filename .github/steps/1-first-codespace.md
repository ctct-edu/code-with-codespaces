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

[原文](https://github.com/skills/code-with-codespaces/blob/main/.github/steps/1-first-codespace.md)
