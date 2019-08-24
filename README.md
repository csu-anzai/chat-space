# About Chat space

以下の機能を実装したチャットアプリケーション
- 新規登録機能
- グループ内でのチャット機能
- 複数人によるグループチャット機能
- チャット相手の検索機能
- チャットグループへのユーザー招待機能
- チャットの履歴表示機能
- 画像送信機能
- チャットの自動更新
[Chat space](https://chat-space-sample.herokuapp.com/)

# Database design
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_name|string|null: false, unique: true|
|email|string|null: false, unique: true|
|password|string|null: false|
### Association
- has_many : groups, through: :users_groups
- has_many : messages

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group_name|string|null: false, unique: true|
|user_id|integer|null: false, foreign_key: true|
|message_id|integer|null: false, foreign_key: true|
### Association
- has_many : users, through: :users_groups
- has_many : messages

## users_groupsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to : user
- belongs_to : group

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
|file_id|integer||
|file_name|string||
### Association
- belongs_to : user
- belongs_to : group

# Creator

**Seiko Yamada**
- スタイル: EXP短期(福岡)
- 受講期: TECH::CAMP EXPERT 第59期