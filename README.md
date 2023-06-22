# アプリケーション名
TasKey
<br>

# アプリケーション概要
ルーティン化したいタスクを入力すると自動で細かい手順が表示される。また、手動で手順を設定することも可能。注意欠如・多動症の方向けのタスク管理アプリとなっており、シンプルな構造となっている。
<br>

# URL
作成中
<br>

# テスト用アカウント
- Basic認証パスワード:2222
- Basic認証ID:admin
- メールアドレス:
- パスワード :
<br>

# 利用方法
1. トップページの上部からユーザー新規登録を行う。
2. タスク一覧画面上部のマイページにあるタスク内容登録・編集機能からカテゴリ・タスク名・タスク内容を設定することができる。
※デフォルトで設定してあるものについては、自動でタスク内容が設定される。
3. その日のルーティンタスクを終わらせたらタスク一覧画面の日付部分にチェックを入れることができる。
<br>

# アプリケーションを作成した背景
ADHDは特性によって様々だが、毎日のタスクがどうしてもできないという人も多い。頑張っているのに、なぜできないのだろうかと辛い思いをする人もいる。私自身も様々なタスク管理アプリを使用してきたが、使いこなせなかった。ADHDだからこそ、こんな機能がついているタスク管理アプリがあったら良いのにと考え、このアプリケーションを作成した。
<br>

# 洗い出した要件
[要件定義シート](https://docs.google.com/spreadsheets/d/1Pw4UgZbZQPtAvJeBD6fwdRlCuQnM-vq9sFGCUHvFIew/edit?usp=sharing)
<br>

# 実装した機能についての画像やGIFおよびその説明
~~画像やGIF、説明を記載~~※作成中
<br>

# 実装予定の機能
- 要件定義シートに記載したもの以外にも認知行動療法を用いた機能を追加したい。
<br>

# データベース設計
![TasKey_ER_500](https://github.com/OwadaBaku/taskey/assets/82127461/8069a103-b12b-4f34-8f66-a98beee5b0aa)

<br>

# 画面遷移図
![TasKey_transition_500](https://github.com/OwadaBaku/taskey/assets/82127461/de55d5da-95b6-4be7-b112-360da06497c2)

<br>

### usersテーブル
| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| name               | string | null: false               |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |

#### Association
	has_many :checks
	has_many :adverts
	has_many :tasks
	has_one :cookie

### tasks テーブル
| Column       	   		 | Type       | Options                        |
| -------------------- | ---------- | ------------------------------ |
| user           	  	 | references | null: false, foreign_key: true |
| category             | integer    | null: false                    |
| task                 | integer    | null: false                    |
| detail               | integer    | null: true                     |

#### Association
	belongs_to :user
	has_many :checks

### checksテーブル
| Column        | Type       | Options                        |
| ------------- | ---------- | ------------------------------ |
| user          | references | null: false, foreign_key: true |
| task          | references | null: false, foreign_key: true |
| day           | references | null: false                    |
| check         | references | null: false                    |

#### Association
	belongs_to :task
	belongs_to :user

### cookie テーブル
| Column        | Type       | Options                        |
| ------------- | ---------- | ------------------------------ |
| user          | references | null: false, foreign_key: true |
| cookie        | string     | null: false                    |

#### Association
	belongs_to :user

### adverts テーブル
| Column        | Type       | Options                        |
| ------------- | ---------- | ------------------------------ |
| user          | references | null: false, foreign_key: true |
| cookie        | string     | null: false                    |

#### Association
	belongs_to :user
	belongs_to :cookie

# 開発環境
- フロントエンド
- バックエンド
- テスト用アカウント
- テキストエディタ
- タスク管理
<br>

# ローカルでの動作方法
以下のコマンドを順に実行
% git clone [https://github.com/OwadaBaku/taskey.git](https://github.com/OwadaBaku/taskey.git)<br>
% cd taskey<br>
% bundle install<br>
% yarn install
