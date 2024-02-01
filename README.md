# テーブル設計

## users テーブル

| Column             | Type   | Options                       |
| ------------------ | ------ | ----------------------------- |
| email              | string | null: false, uniqueness: true |
| encrypted_password | string | null: false                   |
| nickname           | string | null: false                   |

### Association
has_many :tweets
has_many :comments

## tweets テーブル

| Column        | Type       | Options                        |
| ------------- | ---------- | ------------------------------ |
| plaice-name   | string     | null: false                    |
| memo          | text       | null: false                    |
| prefecture_id | integer    | null: false                    |
| condition_id  | integer    | null: false                    |
| again_id      | integer    | null: false                    |
| user          | references | null: false, foreign_key: true |

### Association
belong_to :user
has_many :comments

## comments テーブル

| Column     | Type       | Options                        |
| ---------- | ---------- | ------------------------------ |
| text       | text       | null: false                    |
| tweet      | references | null: false, foreign_key: true |
| user       | references | null: false, foreign_key: true |

### Association
has_many :comments
belong_to :user