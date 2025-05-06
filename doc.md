## 0. 環境構築

ここでは、team411でGit/GitHubを使用していくために必要な環境構築をしていきます。
もうすでに、環境ができている人は軽く読み飛ばしてください。

### 0.1. GitHubアカウントの作成

[GitHub](https://github.com/)にアクセスし、「Sign Up」からアカウントを作成してください。
すでにGitHubアカウントを持っている人はそのアカウントを使用してください。

ここで登録時に使用したメールアドレスを覚えておいてください。
team411の組織やリポジトリに招待されたときは、登録したメールアドレスに連絡が来ます。
普段よく使うメールアドレスが良いでしょう。

### 0.2. Gitのインストール

まず、今回の研修で使用するメインのアプリケーションである、`git`をインストールします。
それぞれ自分が使っているOSの方法を参考にインストールしてください。
#### Windowsの場合
`Win + R`キーを押下し、`powershell`と入力して`Enter`（Power Shellが開きます）。
以下のコマンドを入力し実行。

```powershell
winget install Git.Git
```

「このアプリがデバイスに変更を加えることを許可しますか？」と聞かれるので「はい」を選択。
実行が終わったらインストールは完了です。

#### MacOSの場合
「ターミナル」アプリを起動します。
まず、以下のコマンドを入力し実行して`brew`をインストールします。

```zsh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

少し時間がかかると思いますが、待ちます。
実行が終わったら次に`brew`を使って`git`をインストールします。

以下のコマンドを入力し、実行してください。

```zsh
brew install git
```

実行が終わったらインストールは完了です。

#### Linux (Debian系)の場合
ターミナルのアプリケーションを開き以下のコマンドを実行してください。

```zsh
sudo apt update
sudo apt install git
```

実行が終わったらインストールは完了です。

### 0.3. GitHub Cliのインストール

次に、先ほど作成したGitHubアカウントとの連携を簡単に行うためのアプリケーション`GitHub CLI`をインストールします。
これも同様に、それぞれ自分が使っているOSの方法を参考にインストールしてください。

#### Windowsの場合
`Win + R`キーを押下し、`powershell`と入力して`Enter`（Power Shellが開きます）。
以下のコマンドを入力し実行。

```powershell
winget install GitHub.cli
```

「このアプリがデバイスに変更を加えることを許可しますか？」と聞かれるので「はい」を選択。
実行が終わったらインストールは完了です。

#### MacOSの場合
「ターミナル」アプリを起動します。
以下のコマンドを入力し、実行してください。

```zsh
brew install gh
```

実行が終わったらインストールは完了です。

#### Linux (Debian系)の場合
ターミナルのアプリケーションを開き以下のコマンドを実行してください。

```zsh
sudo apt update
sudo apt install gh
```

実行が終わったらインストールは完了です。

### 0.4. ローカルのGitを自分のGitHubアカウントと連携

ターミナルアプリケーションを開き、以下のコマンドを実行して、先ほど作成したGitHubアカウントとの連携を行います。

```zsh
gh auth login
```

すると次のように表示されるので、そのまま`Enter`を押します。
（ログインに使うアカウントの種類を聞かれています。今回はGitHubを使用するのでそのままそれを選択します）

```zsh
? Where do you use GitHub?  [Use arrows to move, type to filter]
> GitHub.com
  Other
```

次に、認証の方法を聞かれるので、下矢印キーを押して「ssh」を選択し`Enter`を押します。

```zsh
? What is your preferred protocol for Git operations on this host?  [Use arrows to move, type to filter]
  HTTPS
> SSH
```

続けて、いくつか質問をされますので、そのまま`Enter`を押します。

```zsh
? Generate a new SSH key to add to your GitHub account? (Y/n)
? Enter a passphrase for your new SSH key (Optional):                            ? Title for your SSH key: (GitHub CLI)
```

次のように聞かれたら、「Login with a web browser」を選択し、`Enter`を押します。

```zsh
? How would you like to authenticate GitHub CLI?  [Use arrows to move, type to filter]
> Login with a web browser
  Paste an authentication token
```

`Press Enter to open https://github.com/login/device in your browser...`と言われますので、`Enter`を押してGitHubにログインする画面を開きます。

自分のGitHubアカウントで「Continue」します。

![[Pasted image 20250506195132.png]]

すると、次のような画面で、ワンタイムコードの入力を求められますので、先ほどコマンドを実行したターミナルに表示されているワンタイムコードを入力し、「Continue」します。

![[Pasted image 20250506195531.png]]

ワンタイムコード

![[Pasted image 20250506195455.png]]

これで、GitHubアカウントとの連携作業は完了です。

### 0.5. VSCodeでGitを使う

GitはCLI（Command Line Interface、雑に言うと黒い画面）で使うものですが、VSCodeに拡張機能を入れることで快適に使用することができます。
ここでは、VSCodeでのセットアップ方法を紹介します。CLIで使いたい人、VSCodeではないエディタを使用している人は、各自が使いやすい環境を作ってください。

TODO: VSCodeの拡張の話を追加

#### 0.6. (推奨) GitHub Copilotを使用するため学生プランの申請

TODO: GitHub Student Planの申請方法を追加

## 1. Git

### 1.0. Gitとは
ここまで、Gitという言葉を一切説明せずに使ってきましたが、そもそもGitとは何でしょうか。

簡単に説明すると、

>Gitは、「**いつ、誰が、どのファイルをどう変更したか**」を記録し、  
>必要に応じて**過去の状態に戻せる**、**他人との作業の違いを見つけて統合できる**ようにするツール。

詳しくは、Gitの公式ドキュメントに書いてありますので、そちらを読んでみてください。

[Git - What is Git?](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F)

それでは、Gitがどのようなものなのかを、「概念」と「使い方」に分けてみていきましょう。

### 1.1. Gitの基本概念

Gitがどのような概念で構成されているのかを紹介します。
ここで完璧に理解する必要はありません。次の章以降で実際に操作していく中で、単語の意味がわからなかったら戻ってくる「用語辞典」のように使ってください。
#### リポジトリ

#### コミット

#### ステージングエリア

#### ワーキングディレクトリ

#### ブランチ

#### HEAD

#### マージ

#### リベース

#### コンフリクト


### 1.2. 基本コマンド

それでは、実際に手を動かして使ってみましょう。
今回の研修で使用するリポジトリがありますので、以下のコマンドを実行して、cloneしましょう。

```zsh
git clone git@hogehoge.git
```

`git`で使用する基本的なコマンドについて、

- 役割
- 使い方
- VSCodeの拡張機能との対応

について解説していきます。

#### `git init`（？）

#### `git clone`

#### `git add`

#### `git stash`

#### `git commit -m "message"`

#### `git reset`

#### `git revert`

#### `git diff`

#### `git log`(？)

#### `git branch`

#### `git switch`

#### `git merge`

#### `git remote`

#### `git fetch`

#### `git pull`

#### `git push`


### 1.3. その他知っておくと便利なこと

#### `.gitignore`

#### `.gitkeep`

#### `.gitignore`を変更したのに適用されない時


## 2. GitHub
### 2.0. GitHubとは？
GitHubとは、何でしょうか？

簡単に説明すると、

> Gitで管理されたコードをインターネット上に置き、協力して開発できるWebサービス

です。似たようなものにGitLabなどもあります。
こちらについても気になる人は、GitHubの公式ドキュメントを覗いてみてください。

[About Github and Git - About GitHub](https://docs.github.com/en/get-started/start-your-journey/about-github-and-git#about-github)

### 2.1. GitHubを使った開発の流れ

ここでは、実際にteam411で行われている開発の流れを、実際に手を動かしながら学んでいきます。

#### リポジトリをクローン（もしくは新しく作成）する
#### Issueを立てる

#### ブランチを切る

#### コミット・プッシュする

#### Pull Request(PR)を作成する

#### レビュー

#### マージ

#### Issue・PRのクローズ

### 2.2. その他GitHubでできること
#### GitHub Actions