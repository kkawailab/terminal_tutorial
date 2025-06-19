# Git入門 - 各環境での使い方

## Gitとは

Gitは分散型バージョン管理システムで、ファイルの変更履歴を記録し、複数人での共同作業を可能にします。このチュートリアルでは、各環境（DOSプロンプト、PowerShell、Mac）でのGitの基本的な使い方を学びます。

## Gitのインストール

### Windows（DOSプロンプト・PowerShell）
1. [Git for Windows](https://gitforwindows.org/)からインストーラーをダウンロード
2. インストーラーを実行（デフォルト設定で問題ありません）
3. インストール後、新しいターミナルを開いて確認：
```cmd
git --version
```

### Mac
macOSには通常Gitがプリインストールされています。確認方法：
```bash
git --version
```

もしインストールされていない場合：
```bash
# Homebrewがインストールされている場合
brew install git

# または、Xcodeコマンドラインツールをインストール
xcode-select --install
```

## Git共通コマンド（全環境共通）

### 1. 初期設定

#### ユーザー名とメールアドレスの設定
```bash
git config --global user.name "あなたの名前"
git config --global user.email "your-email@example.com"
```

#### 設定の確認
```bash
git config --list
```

### 2. リポジトリの作成と操作

#### 新規リポジトリの作成
```bash
git init
```

#### 既存リポジトリのクローン
```bash
git clone https://github.com/username/repository.git
```

#### ファイルの状態を確認
```bash
git status
```

### 3. 基本的なワークフロー

#### ファイルをステージングエリアに追加
```bash
git add ファイル名.txt
# または全ファイル
git add .
```

#### コミット
```bash
git commit -m "コミットメッセージ"
```

#### 変更履歴の確認
```bash
git log
# 簡潔に表示
git log --oneline
```

### 4. ブランチ操作

#### ブランチの一覧表示
```bash
git branch
```

#### 新しいブランチを作成
```bash
git branch 新しいブランチ名
```

#### ブランチを切り替え
```bash
git checkout ブランチ名
# または作成と同時に切り替え
git checkout -b 新しいブランチ名
```

#### ブランチをマージ
```bash
git merge ブランチ名
```

### 5. リモートリポジトリとの連携

#### リモートリポジトリを追加
```bash
git remote add origin https://github.com/username/repository.git
```

#### リモートリポジトリにプッシュ
```bash
git push origin main
```

#### リモートリポジトリから取得
```bash
git pull origin main
```

## 環境別の注意点とテクニック

### DOSプロンプトでの使用

#### 日本語ファイル名の文字化け対策
```cmd
git config --global core.quotepath false
```

#### ログの文字化け対策
```cmd
set LESSCHARSET=utf-8
```

### PowerShellでの使用

#### Git用のPowerShellモジュール（posh-git）のインストール
```powershell
Install-Module posh-git -Scope CurrentUser
Import-Module posh-git
```

#### エイリアスの設定例
```powershell
Set-Alias g git
```

### Mac（bash/zsh）での使用

#### .gitignoreのグローバル設定
```bash
touch ~/.gitignore_global
git config --global core.excludesfile ~/.gitignore_global
```

#### 便利なエイリアス設定（~/.bashrcまたは~/.zshrcに追加）
```bash
alias gs='git status'
alias ga='git add'
alias gc='git commit'
alias gp='git push'
alias gl='git log --oneline'
```

## よく使うGitコマンドの組み合わせ

### 1. 作業の開始から完了まで
```bash
# 最新の状態を取得
git pull origin main

# 新しいブランチで作業
git checkout -b feature/new-feature

# 作業後、変更を確認
git status

# 変更をステージング
git add .

# コミット
git commit -m "新機能を追加"

# リモートにプッシュ
git push origin feature/new-feature
```

### 2. 間違えたときの対処

#### 直前のコミットメッセージを修正
```bash
git commit --amend -m "新しいコミットメッセージ"
```

#### ステージングを取り消し
```bash
git reset HEAD ファイル名.txt
```

#### 変更を破棄（注意！）
```bash
git checkout -- ファイル名.txt
```

## 練習問題

### 問題1
任意のディレクトリで新しいGitリポジトリを初期化し、ユーザー名とメールアドレスを設定してください。

### 問題2
「hello.txt」というファイルを作成し、「Hello, Git!」と書き込んで、最初のコミットを作成してください。

### 問題3
「develop」という新しいブランチを作成し、そのブランチに切り替えてください。

### 問題4
「hello.txt」に「This is develop branch」という行を追加し、変更をコミットしてください。

### 問題5
mainブランチに戻り、developブランチの変更をマージしてください。

---

## 練習問題の解答

### 解答1
```bash
mkdir git-practice
cd git-practice
git init
git config user.name "Your Name"
git config user.email "your-email@example.com"
```

### 解答2
```bash
echo "Hello, Git!" > hello.txt
git add hello.txt
git commit -m "最初のコミット"
```

### 解答3
```bash
git branch develop
git checkout develop
# または
git checkout -b develop
```

### 解答4
```bash
echo "This is develop branch" >> hello.txt
git add hello.txt
git commit -m "developブランチでの変更"
```

### 解答5
```bash
git checkout main
git merge develop
```

## まとめ

Gitは最初は複雑に感じるかもしれませんが、基本的なコマンドを覚えれば日常的な作業には十分対応できます。各環境での使い方に大きな違いはありませんが、それぞれの環境に合わせた設定やツールを活用することで、より快適にGitを使うことができます。

重要なポイント：
- コミットする前に必ず `git status` で状態を確認
- 意味のあるコミットメッセージを書く
- ブランチを活用して作業を整理
- 定期的にリモートリポジトリと同期

実際のプロジェクトで使いながら、徐々に高度な機能も覚えていきましょう。