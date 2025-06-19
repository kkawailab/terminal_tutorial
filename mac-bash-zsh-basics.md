# Mac - bash/zsh編

## bashとzshとは

- **bash（Bourne Again Shell）**: 長年使われてきた標準的なシェル
- **zsh（Z Shell）**: macOS Catalina以降のデフォルトシェル。bashと互換性があり、より多機能

### ターミナルの起動方法

1. **方法1**: `Command + Space` でSpotlightを開き「Terminal」と入力
2. **方法2**: Finderで「アプリケーション」→「ユーティリティ」→「ターミナル」
3. **方法3**: Launchpadから「ターミナル」を選択

### 現在のシェルを確認
```bash
echo $SHELL
```

## 基本的なコマンド

### 1. ディレクトリの操作

#### 現在のディレクトリを確認
```bash
pwd
```

#### ディレクトリの内容を表示
```bash
ls
```

#### 詳細情報付きで表示
```bash
ls -l
```

#### 隠しファイルも含めて表示
```bash
ls -la
```

#### ディレクトリを移動
```bash
cd ディレクトリ名
```

#### ホームディレクトリに移動
```bash
cd ~
# または単に
cd
```

#### 一つ上のディレクトリに移動
```bash
cd ..
```

#### 前のディレクトリに戻る
```bash
cd -
```

### 2. ファイルとディレクトリの作成・削除

#### ディレクトリを作成
```bash
mkdir フォルダ名
```

#### 階層的にディレクトリを作成
```bash
mkdir -p parent/child/grandchild
```

#### 空のファイルを作成
```bash
touch ファイル名.txt
```

#### ファイルを削除
```bash
rm ファイル名.txt
```

#### ディレクトリを削除（空の場合）
```bash
rmdir フォルダ名
```

#### ディレクトリを削除（中身も含めて）
```bash
rm -r フォルダ名
```

### 3. ファイルの操作

#### ファイルの内容を表示
```bash
cat ファイル名.txt
```

#### ファイルの内容をページ単位で表示
```bash
less ファイル名.txt
# qキーで終了
```

#### ファイルの先頭を表示
```bash
head ファイル名.txt
head -n 5 ファイル名.txt  # 先頭5行
```

#### ファイルの末尾を表示
```bash
tail ファイル名.txt
tail -n 5 ファイル名.txt  # 末尾5行
```

#### ファイルをコピー
```bash
cp 元ファイル.txt コピー先ファイル.txt
```

#### ディレクトリを再帰的にコピー
```bash
cp -r 元ディレクトリ コピー先ディレクトリ
```

#### ファイルを移動・名前変更
```bash
mv 元ファイル.txt 新しいファイル.txt
```

### 4. テキスト処理

#### テキストをファイルに書き込む
```bash
echo "Hello, World!" > hello.txt
```

#### テキストをファイルに追記
```bash
echo "追加のテキスト" >> hello.txt
```

#### ファイル内のテキストを検索
```bash
grep "検索語" ファイル名.txt
```

#### ファイル内のテキストを置換（macOSの場合）
```bash
sed -i '' 's/古いテキスト/新しいテキスト/g' ファイル名.txt
```

### 5. システム情報とプロセス

#### コマンドのマニュアルを表示
```bash
man コマンド名
# qキーで終了
```

#### 画面をクリア
```bash
clear
# または Ctrl + L
```

#### 現在の日付と時刻を表示
```bash
date
```

#### ディスク使用量を確認
```bash
df -h
```

#### 実行中のプロセスを表示
```bash
ps aux
```

#### リアルタイムでプロセスを監視
```bash
top
# qキーで終了
```

## 環境変数とパス

### 環境変数を表示
```bash
echo $変数名
```

例：
```bash
echo $PATH
echo $HOME
echo $USER
```

### すべての環境変数を表示
```bash
env
```

### 環境変数を設定（一時的）
```bash
export MY_VAR="値"
```

## シェルの便利な機能

### 1. タブ補完
ファイル名やコマンドの途中でTabキーを押すと自動補完

### 2. コマンド履歴
```bash
history
```

上下矢印キーで過去のコマンドを呼び出し

### 3. ワイルドカード
```bash
ls *.txt      # .txtで終わるファイル
ls test*      # testで始まるファイル
ls test?.txt  # test + 1文字 + .txt
```

### 4. パイプとリダイレクト
```bash
ls -la | grep txt           # パイプ：出力を次のコマンドへ
ls -la > filelist.txt       # リダイレクト：出力をファイルへ
ls -la | grep txt > result.txt  # 組み合わせ
```

### 5. エイリアス（bashとzsh共通）
```bash
alias ll='ls -la'
alias ..='cd ..'
```

## zsh特有の便利機能

### 1. 高度な補完機能
```bash
cd /u/lo/b[Tab]  # /usr/local/bin に展開
```

### 2. グロブ展開
```bash
ls **/*.txt  # サブディレクトリも含めて.txtファイルを検索
```

## 練習問題

### 問題1
デスクトップに移動して、「mac-practice」という名前のディレクトリを作成し、その中に移動してください。

### 問題2
「test.txt」というファイルを作成し、「Hello from Mac Terminal!」というテキストを書き込んでください。

### 問題3
現在のディレクトリに「folder1」「folder2」「folder3」という3つのディレクトリを一度に作成してください。

### 問題4
「test.txt」を各フォルダにコピーし、その後すべての.txtファイルを検索して表示してください。

### 問題5
現在のディレクトリとサブディレクトリ内のすべてのファイルとディレクトリを詳細情報付きで表示し、その結果を「directory_tree.txt」に保存してください。

---

## 練習問題の解答

### 解答1
```bash
cd ~/Desktop
mkdir mac-practice
cd mac-practice
```

### 解答2
```bash
echo "Hello from Mac Terminal!" > test.txt
# または
touch test.txt
echo "Hello from Mac Terminal!" > test.txt
```

### 解答3
```bash
mkdir folder1 folder2 folder3
# または
mkdir folder{1..3}
```

### 解答4
```bash
cp test.txt folder1/
cp test.txt folder2/
cp test.txt folder3/
find . -name "*.txt"
# または
ls **/*.txt  # zshの場合
```

### 解答5
```bash
ls -laR > directory_tree.txt
# または
find . -ls > directory_tree.txt
```

## まとめ

MacのターミナルでbashやzshはUNIX系のコマンドを使用し、Windowsとは異なる操作体系を持っています。基本的なファイル操作からテキスト処理、プロセス管理まで、様々なタスクを効率的に実行できます。

zshはbashの機能を拡張し、より便利な補完機能やグロブ展開を提供しています。日常的な作業では、タブ補完やコマンド履歴を活用することで、作業効率を大幅に向上させることができます。

ターミナルを使いこなすことで、GUIでは難しい複雑な操作や自動化が可能になります。まずは基本的なコマンドから始めて、徐々に高度な機能を学んでいきましょう。