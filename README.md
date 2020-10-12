# テーブル設計

## users テーブル

| Column       | Type   | Options         |
| ------------ | ------ | --------------- |
| nickname     | string | null: false     |
| email        | string | null: false, uniqueness: true |
| password     | string | null: false, uniqueness: true |
| first_name   | string | null: false     |
| last_name    | string | null: false     |
| first_name_kana   | string | null: false     |
| last_name_kana    | string | null: false     |
| birth_date   | date   | null: false     |

### Association
- belongs_to :item
- belongs_to :purchase


## items テーブル

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| user   | references | null: false, foreign_key: true |
| name   | string | null: false |
| price  | integer | null: false |

### Association
- has_many :user
- has_one :purchase

## purchases テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| user    | references | null: false, foreign_key: true |
| item    | references | null: false, foreign_key: true |

### Association
- has_many :user
- has_one :item
