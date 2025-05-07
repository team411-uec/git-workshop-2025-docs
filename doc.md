## 0. 環境構築

ここでは、team411 で Git/GitHub を使用していくために必要な環境構築をしていきます。
もうすでに、環境ができている人は軽く読み飛ばしてください。

### 0.1. GitHub アカウントの作成

[GitHub](https://github.com/)にアクセスし、「Sign Up」からアカウントを作成してください。
すでに GitHub アカウントを持っている人はそのアカウントを使用してください。

ここで登録時に使用したメールアドレスを覚えておいてください。
team411 の組織やリポジトリに招待されたときは、登録したメールアドレスに連絡が来ます。
普段よく使うメールアドレスが良いでしょう。

### 0.2. Git のインストール

まず、今回の研修で使用するメインのアプリケーションである、`git`をインストールします。
それぞれ自分が使っている OS の方法を参考にインストールしてください。

#### Windows の場合

`Win + R`キーを押下し、`powershell`と入力して`Enter`（Power Shell が開きます）。
以下のコマンドを入力し実行。

```powershell
winget install Git.Git
```

「このアプリがデバイスに変更を加えることを許可しますか？」と聞かれるので「はい」を選択。
実行が終わったらインストールは完了です。

#### MacOS の場合

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

#### Linux (Debian 系)の場合

ターミナルのアプリケーションを開き以下のコマンドを実行してください。

```zsh
sudo apt update
sudo apt install git
```

実行が終わったらインストールは完了です。

### 0.3. GitHub Cli のインストール

次に、先ほど作成した GitHub アカウントとの連携を簡単に行うためのアプリケーション`GitHub CLI`をインストールします。
これも同様に、それぞれ自分が使っている OS の方法を参考にインストールしてください。

#### Windows の場合

`Win + R`キーを押下し、`powershell`と入力して`Enter`（Power Shell が開きます）。
以下のコマンドを入力し実行。

```powershell
winget install GitHub.cli
```

「このアプリがデバイスに変更を加えることを許可しますか？」と聞かれるので「はい」を選択。
実行が終わったらインストールは完了です。

#### MacOS の場合

「ターミナル」アプリを起動します。
以下のコマンドを入力し、実行してください。

```zsh
brew install gh
```

実行が終わったらインストールは完了です。

#### Linux (Debian 系)の場合

ターミナルのアプリケーションを開き以下のコマンドを実行してください。

```zsh
sudo apt update
sudo apt install gh
```

実行が終わったらインストールは完了です。

### 0.4. ローカルの Git を自分の GitHub アカウントと連携

ターミナルアプリケーションを開き、以下のコマンドを実行して、先ほど作成した GitHub アカウントとの連携を行います。

```zsh
gh auth login
```

すると次のように表示されるので、そのまま`Enter`を押します。
（ログインに使うアカウントの種類を聞かれています。今回は GitHub を使用するのでそのままそれを選択します）

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

`Press Enter to open https://github.com/login/device in your browser...`と言われますので、`Enter`を押して GitHub にログインする画面を開きます。

自分の GitHub アカウントで「Continue」します。

![](./github-account-selection.png)

すると、次のような画面で、ワンタイムコードの入力を求められますので、先ほどコマンドを実行したターミナルに表示されているワンタイムコードを入力し、「Continue」します。

![](./github-enter-onetime-code.png)

ワンタイムコード

![](./github-check-onetime-code.png)

これで、GitHub アカウントとの連携作業は完了です。

### 0.5. VSCode で Git を使う

Git は CLI（Command Line Interface、雑に言うと黒い画面）で使うものですが、VSCode に拡張機能を入れることで快適に使用することができます。
ここでは、VSCode でのセットアップ方法を紹介します。CLI で使いたい人、VSCode ではないエディタを使用している人は、各自が使いやすい環境を作ってください。

TODO: VSCode の拡張の話を追加

#### 0.6. (推奨) GitHub Copilot を使用するため学生プランの申請

TODO: GitHub Student Plan の申請方法を追加

## 1. Git

### 1.0. Git とは

ここまで、Git という言葉を一切説明せずに使ってきましたが、そもそも Git とは何でしょうか。

簡単に説明すると、

> Git は、「**いつ、誰が、どのファイルをどう変更したか**」を記録し、  
> 必要に応じて**過去の状態に戻せる**、**他人との作業の違いを見つけて統合できる**ようにするツール。

詳しくは、Git の公式ドキュメントに書いてありますので、そちらを読んでみてください。

[Git - What is Git?](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F)

それでは、Git がどのようなものなのかを、「概念」と「使い方」に分けてみていきましょう。

### 1.1. Git の基本概念

Git がどのような概念で構成されているのかを紹介します。
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

ここでは、`git`で使用する基本的なコマンドについて、

- 役割
- 使い方
- VSCode の拡張機能との対応

について解説していきます。
後で演習で手を動かしながら使っていくので、流し読みしてもらって大丈夫です。
わからないことがあれば、戻ってくる、という感じで。重要なものには「●」がついています。これだけは読むようにしてください。

#### `git clone` ●

リモートリポジトリをローカルに複製することができます。

```zsh
git clone クローンしたいリポジトリ
```

のように使います。

#### `git add` ●

変更をステージングエリアに追加し、コミットの対象にします。

VSCode では、「+」のボタンを押すことで追加できます。
![](./git-add.png)

「変更」と書いてある場所をホバーすると、すべてを add することができます。
![](./git-add-all.png)

CLI で使用するには、

```zsh
git add 対象とするファイル
```

のように使います。作業したすべてのファイルをステージするには

```zsh
git add .
```

のようにします。`.`は現在のディレクトリを指すので、すべてのファイルが追加される、という仕組みです。

#### `git commit` ●

その名の通り、コミットを作成することができます。これによりステージされた変更が記録されます。

VSCode では、入力欄にコミットメッセージを入力し、コミットボタンを押すことでコミットができます。

![](./git-commit.png)

CLI では以下のように使用します。

```zsh
git commit -m "コミットメッセージ"
```

#### `git push` ●

ローカルリポジトリの変更をリモートリポジトリに反映するコマンドです。
VSCodeでは、コミットした後に

CLI で使うのは少し難しいですが、次のように使います。

```zsh
git push リモートリポジトリ名 ブランチ名
```

リモートリポジトリ名は`origin`であることが多いです。
具体的には

```zsh
git push origin main
```

のように使います（`main`ブランチにコミットする例）。

#### `git switch` ●

ブランチの作成、切り替えを行うことができます。

```zsh
# ブランチの作成
git switch -c ブランチ名

# ブランチの切り替え
git switch ブランチ名
```

#### `git pull` ●

リモートリポジトリから変更を取得し、その内容をローカルブランチにマージします。
マージされる対象は現在作業中のブランチです。

```zsh
git pull
```

と使用します。

#### `git fetch`

リモートリポジトリの最新の情報を取得します。
ローカルリポジトリにマージはされません。

```zsh
git fetch
```

とすることで、リモートのすべての変更を取得することができます。

#### `git merge`

別のブランチの内容を現在のブランチにマージするコマンドです。

ブランチ A にいる状態で

```zsh
git merge B
```

のようにすると、ブランチ B の内容が現在作業しているブランチ A にマージされます。

#### `git stash`

ステージしていない作業中の変更を一時退避する機能です。

```zsh
git stash
```

でスタッシュすることができます。スタッシュに説明文を追加するには、

```zsh
git stash save "作業内容の説明"
```

のようにします。スタッシュした変更の一覧は

```zsh
git stash list
```

で見ることができ、`stash@{0}`、`stash@{1}`のような形式で表示されます。
スタッシュした内容を現在の作業に反映させる方法は 2 種類あります。
まず、スタッシュした内容を復元して削除する`pop`という方法で、

```zsh
# 最新のstashを適用して削除
git stash pop

# N番目のstashを適用して削除
git stash pop stash@{N}
```

のように使用します。もう一つの`apply`は、`pop`に似ていますが、こちらは変更を復元した後削除をしないという方法です。

```zsh
# 最新のstashを適用
git stash apply

# N番目のstashを適用
git stash apply stash@{N}
```

のように使用します。また、スタッシュした内容がいらなくなった時は削除することができます。

```zsh
# N番目のstashを削除
git stash drop stash@{N}

# すべてのstashを削除
git stash clear
```

のように使うことで、コミットメッセージをつけ、コミットすることができます。

#### `git reset`

コミットやステージの状態を過去の状態に戻すことができます。
以下のようなオプションがあります。

- `--hard`: add、commit、作業内容をすべて削除します
- `--mixed`: add と commit を取り消します
- `--soft`: commit のみ取り消します

また、どのコミットまで戻したいかを指定でき、`^`や`~`をつけることで直前のコミットを表すことができます（例: `HEAD^`）。

#### `git revert`

指定したコミットを「打ち消す」新しいコミットを作成します。

```zsh
git revert コミットID
```

のように使います。

### 1.3 練習

### 1.4. その他知っておくと便利なこと

#### `.gitignore`

#### `.gitkeep`

#### `.gitignore`を変更したのに適用されない時

#### commitlint を使ったコミットメッセージのチェック

#### pre-commit について

#### GPG を用いたコミットの認証

## 2. GitHub

### 2.0. GitHub とは？

GitHub とは、何でしょうか？

簡単に説明すると、

> Git で管理されたコードをインターネット上に置き、協力して開発できる Web サービス

です。似たようなものに GitLab などもあります。
こちらについても気になる人は、GitHub の公式ドキュメントを覗いてみてください。

[About Github and Git - About GitHub](https://docs.github.com/en/get-started/start-your-journey/about-github-and-git#about-github)

### 2.1. GitHub を使った開発の流れ

ここでは、実際に team411 で行われている開発の流れを、実際に手を動かしながら学んでいきます。

#### リポジトリをクローン（もしくは新しく作成）する

#### Issue を立てる

#### ブランチを切る

#### コミット・プッシュする

#### Pull Request(PR)を作成する

#### レビュー

#### マージ

#### Issue・PR のクローズ

### 2.2. その他 GitHub でできること

#### GitHub Actions

```

```

```

```
