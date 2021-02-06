# テーブル設計

## users テーブル

| Column     | Type   | Options     |
| --------   | ------ | ----------- |
| email      | string | null: false |
| password   | string | null: false |
| name       | string | null: false |
| profile    | text   | null: false |
| occupation | text   | null: false |
| position   | text   | null: false |

### Association
- has_many  :prototypes
- has_many  :comments, through: prototypes

## comments テーブル

| Column    | Type       | Options     |
| --------- | ---------- | ----------- |
| text      | string     | null: false |
| user      | references | null: false |
| prototype | references | null: false |

### Association
- belongs_to :users
- belongs_to :prototypes

## prototypes テーブル

| Column     | Type          | Options                        |
| ---------- | ------------- | ------------------------------ |
| title      | string        | null: false                    |
| catch_copy | text          | null: false                    |
| concept    | test          | null: false                    |
| image      | ActiveStorage | null: false, foreign_key: true |
| user       | references    | null: false, foreign_key: true |

### Association
- belongs_to :users
- has_many :comments