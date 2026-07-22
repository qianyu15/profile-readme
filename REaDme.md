# Profile README Generator

GitHubユーザー名を入力するだけで、GitHub APIからプロフィール情報を取得し、プロフィール用の `README.md` を自動生成するWebツールです。

## ✨ このツールの特徴

### 「設定して作る」ではなく「GitHubから取得して作る」

一般的なProfile README Generatorは、ユーザーが名前・自己紹介・スキル・リンクなどをフォームに入力し、テンプレートを組み合わせてREADMEを作成します。

このツールは、その方式とは異なります。

**GitHubユーザー名を入力するだけで、実際のGitHubプロフィールからREADMEを生成します。**

```text
GitHub username
        ↓
GitHub API
        ↓
プロフィール情報を取得
        ↓
リポジトリ情報を取得
        ↓
README.mdを自動生成
```

手動でプロフィール情報を入力する必要はありません。人間が同じ情報を何度も入力するという、コンピューターが存在する理由そのものに反する作業を削減します。

---

## 🚀 主な機能

* GitHubユーザー名だけでREADMEを生成
* GitHubプロフィール情報を自動取得
* GitHubの自己紹介文を反映
* GitHubアカウント作成からの経過年数を自動計算
* 所有している非Forkリポジトリを取得
* 使用言語を自動抽出
* プロジェクト一覧を自動生成
* GitHubプロフィールへのリンクを自動生成
* 公開メールアドレスがある場合は連絡先に追加
* 生成したREADMEをブラウザから直接ダウンロード
* サーバー不要で動作

---

## 🆚 既存のProfile README Generatorとの違い

| 一般的なジェネレーター          | Profile README Generator |
| -------------------- | ------------------------ |
| フォームに大量の情報を入力        | GitHubユーザー名だけ入力          |
| テンプレートを手動で編集         | GitHubの実データから自動生成        |
| 固定されたプロフィール情報        | 現在のGitHubプロフィールを反映       |
| スキルを手動で入力            | リポジトリの使用言語から自動抽出         |
| プロジェクトを手動で追加         | GitHubリポジトリから自動取得        |
| 外部サービスやサーバーが必要な場合がある | ブラウザからGitHub APIを直接利用    |
| 作成後に情報が古くなりやすい       | GitHubの最新データを元に生成        |

### 最大の違い

> **このツールはREADMEを「入力して作る」のではなく、GitHubの実際の活動データから生成する。**

これがこのツールの最大の特徴です。

---

## 🛠️ 使用技術

* HTML
* CSS
* JavaScript
* GitHub REST API

外部フレームワークやビルドツールは使用していません。

単一のHTMLファイルだけで動作するため、非常にシンプルな構成になっています。

---

## 📊 READMEの生成内容

生成されるREADMEには、以下の情報が含まれます。

### プロフィール

GitHubの表示名、またはユーザー名を使用します。

```markdown
# Hi I am username
```

### 自己紹介

GitHubプロフィールに設定されているbioを反映します。

### GitHub利用年数

アカウント作成日から現在までの経過年数を自動計算します。

```markdown
I have been on GitHub for 5 years.
```

### Skills

所有している非Forkリポジトリの主要言語を自動的に抽出します。

```markdown
## Skills

- JavaScript
- Python
- HTML
- CSS
```

### Projects

Forkではないリポジトリをプロジェクトとして一覧化します。

```markdown
## Projects

### project-name

Project description

[View Repository](https://github.com/...)
```

### Contact

GitHubプロフィールへのリンクを生成します。

公開メールアドレスが設定されている場合は、メールアドレスも追加されます。

---

## 💡 使い方

1. GitHubユーザー名を入力
2. `Generate` をクリック
3. GitHub APIからプロフィールとリポジトリ情報を取得
4. READMEのプレビューを確認
5. `Download README.md` をクリック

これだけです。

プロフィール情報を手動でコピーして、リポジトリを確認して、言語を一覧化して、リンクを貼って、READMEを整形する作業を全部やる必要はありません。人間が最も得意とする「同じ情報を何度も転記する作業」を、ブラウザに任せられます。

---

## 🔌 GitHub API

このツールではGitHub REST APIを使用しています。

使用している主なエンドポイントは以下です。

```text
GET /users/{username}
```

GitHubユーザーのプロフィール情報を取得します。

```text
GET /users/{username}/repos
```

ユーザーのリポジトリ一覧を取得します。

取得したデータから、以下の情報をREADMEに反映します。

* ユーザー名
* 表示名
* Bio
* アカウント作成日
* 公開メールアドレス
* リポジトリ
* 使用言語
* リポジトリURL
* プロジェクト説明

---

## 🔒 プライバシー

このツールには独自のバックエンドサーバーはありません。

ブラウザ上のJavaScriptからGitHub APIへ直接アクセスし、取得したデータをREADMEの生成に使用します。

生成されたREADMEもブラウザ内で作成され、ダウンロードされます。

---

## ⚠️ 制限事項

### GitHub APIのレート制限

GitHub APIにはレート制限があります。

短時間に大量のリクエストを行うと、一時的にAPIを利用できなくなる場合があります。

### 取得できる情報は公開情報が中心

GitHub APIから取得できる情報には制限があります。

非公開情報や、GitHubプロフィールに公開されていない情報はREADMEに反映されません。

### リポジトリ数

現在の実装では、最大100件のリポジトリを取得します。

---

## 🔮 今後の予定

* READMEテンプレートの選択
* GitHub Topicsの取得
* Star数・Fork数の表示
* リポジトリの言語割合の表示
* GitHub Statsの追加
* SNSリンクの自動取得
* READMEのカスタマイズ機能
* ダークモード・ライトモード切り替え
* GitHub OAuth対応
* GitHub Actionsによる自動更新

---

## 📄 License

MIT License
