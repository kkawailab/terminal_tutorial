# Windows - PowerShell編

## PowerShellとは

PowerShellは、Microsoftが開発した新しいコマンドラインシェルおよびスクリプト言語です。DOSプロンプトよりも強力で、オブジェクト指向の概念を取り入れています。

### PowerShellの起動方法

1. **方法1**: `Windows + X` キーを押して「Windows PowerShell」を選択
2. **方法2**: スタートメニューで「PowerShell」を検索
3. **方法3**: `Windows + R` キーを押して「powershell」と入力

## 基本的なコマンドレット

PowerShellでは、「動詞-名詞」形式のコマンドレットを使用します。

### 1. ディレクトリ（フォルダ）の操作

#### 現在のディレクトリを確認
```powershell
Get-Location
# または短縮形
pwd
```

#### ディレクトリの内容を表示
```powershell
Get-ChildItem
# または短縮形
ls
dir
```

#### ディレクトリを移動
```powershell
Set-Location フォルダ名
# または短縮形
cd フォルダ名
```

#### 一つ上のディレクトリに移動
```powershell
Set-Location ..
# または
cd ..
```

### 2. ファイルとディレクトリの作成・削除

#### ディレクトリを作成
```powershell
New-Item -ItemType Directory -Name フォルダ名
# または短縮形
mkdir フォルダ名
```

#### ファイルを作成
```powershell
New-Item -ItemType File -Name ファイル名.txt
```

#### ファイルを削除
```powershell
Remove-Item ファイル名.txt
# または短縮形
rm ファイル名.txt
```

#### ディレクトリを削除（中身も含めて）
```powershell
Remove-Item フォルダ名 -Recurse
```

### 3. ファイルの操作

#### ファイルの内容を表示
```powershell
Get-Content ファイル名.txt
# または短縮形
cat ファイル名.txt
type ファイル名.txt
```

#### ファイルをコピー
```powershell
Copy-Item 元ファイル.txt コピー先ファイル.txt
# または短縮形
cp 元ファイル.txt コピー先ファイル.txt
```

#### ファイルを移動・名前変更
```powershell
Move-Item 元ファイル.txt 新しいファイル.txt
# または短縮形
mv 元ファイル.txt 新しいファイル.txt
```

### 4. システム情報とヘルプ

#### コマンドレットのヘルプを表示
```powershell
Get-Help コマンドレット名
```

例：
```powershell
Get-Help Get-ChildItem
Get-Help Get-ChildItem -Examples
```

#### 画面をクリア
```powershell
Clear-Host
# または短縮形
cls
clear
```

#### 現在の日付と時刻を表示
```powershell
Get-Date
```

## PowerShellの特徴的な機能

### 1. パイプライン
コマンドレットの出力を別のコマンドレットに渡す：
```powershell
Get-ChildItem | Where-Object {$_.Name -like "*.txt"}
```

### 2. フィルタリング
特定の条件でファイルを検索：
```powershell
Get-ChildItem -Filter "*.txt"
```

### 3. 変数
```powershell
$myVariable = "Hello, PowerShell"
Write-Host $myVariable
```

### 4. エイリアス
多くのコマンドレットには短縮形（エイリアス）があります：
```powershell
Get-Alias
```

## よく使うテクニック

### 1. ファイルの検索
```powershell
Get-ChildItem -Path C:\ -Filter "*.txt" -Recurse
```

### 2. ファイルサイズでソート
```powershell
Get-ChildItem | Sort-Object Length -Descending
```

### 3. 最新のファイルを表示
```powershell
Get-ChildItem | Sort-Object LastWriteTime -Descending | Select-Object -First 5
```

### 4. テキストをファイルに出力
```powershell
"Hello, World!" | Out-File hello.txt
```

## 練習問題

### 問題1
ホームディレクトリに移動して、「ps-practice」という名前のフォルダを作成してください。

### 問題2
「ps-practice」フォルダの中に、「data1.txt」から「data5.txt」まで5つのファイルを作成してください。（ヒント：1..5の範囲を使用）

### 問題3
現在のディレクトリにあるすべてのファイルを、サイズの大きい順に表示してください。

### 問題4
「data1.txt」に「PowerShell is powerful!」というテキストを書き込んでください。

### 問題5
拡張子が「.txt」のファイルだけを表示し、その結果を「txtfiles.txt」に保存してください。

---

## 練習問題の解答

### 解答1
```powershell
Set-Location ~
New-Item -ItemType Directory -Name ps-practice
# または
cd ~
mkdir ps-practice
```

### 解答2
```powershell
Set-Location ps-practice
1..5 | ForEach-Object { New-Item -ItemType File -Name "data$_.txt" }
```

### 解答3
```powershell
Get-ChildItem | Sort-Object Length -Descending
```

### 解答4
```powershell
"PowerShell is powerful!" | Out-File data1.txt
# または
Set-Content data1.txt "PowerShell is powerful!"
```

### 解答5
```powershell
Get-ChildItem -Filter "*.txt" | Out-File txtfiles.txt
```

## まとめ

PowerShellは、DOSプロンプトよりも高機能で、オブジェクト指向の概念を持つ強力なツールです。パイプラインやフィルタリング機能を使いこなすことで、複雑なタスクも簡単に実行できます。コマンドレットの名前は長いですが、エイリアスを使えば短縮できるので、まずは基本的なコマンドレットとその短縮形を覚えることから始めましょう。