## Step 1　Codespace を起動して変更を送る

1. 自分のコピーで **Code** → **Codespaces** → **Create codespace on main** を選びます。ブラウザーの VS Code がつながるまで待ち、左下に接続先が表示されることを確認します。

   > VS Code に「このフォルダー内のファイルの作成者を信頼しますか？」と表示された場合は、開いているフォルダーが自分の演習用コピーであることを確認し、**フォルダーを信頼して続行** を選びます。
2. **Explorer** で `src/hello.py` を開きます。**TERMINAL** で教材のコマンドを実行し、Node.js、.NET、Python、GitHub CLIのバージョン表示を控えます。
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

### 画面での確認

- 自分のリポジトリ上部の **Code** タブを開き、ファイル一覧の右上にある緑色の **Code** ボタンを押します。メニューの **Codespaces** を選んで作成します。
- VS Code が開いたら左下の接続表示を確認します。左端の書類アイコンが **Explorer**、下部の **TERMINAL** がコマンド入力欄です。見えないときは VS Code の **Terminal → New Terminal** を選びます。
- プッシュ後、元の GitHub タブを再読み込みし、`src/hello.py` に `Hello World!` が表示されることを確認します。

[原文](https://github.com/skills/code-with-codespaces/blob/main/.github/steps/1-first-codespace.md)
