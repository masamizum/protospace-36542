# テーブル設計

## users テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| email              | string | null: false |
| password           | string | null: false |
| name               | string | null: false |
| profile            | text   | null: false |
| occupation         | text   | null: false |
| position           | text   | null: false |

### Association

- has_many :room_users
- has_many :rooms, through: :room_users
- has_many :messages

## phototype テーブル

| Column             | Type         | Options                        |
| ------------------ | ------------ | ------------------------------ |
| title              | string       | null: false                    |
| catch_copy         | text         | null: false                    |
| concept            | text         | null: false                    |
| image              |              | ActiveStrage                   |
| user               | references   | null: false, foreign_key: true |

### Association

- has_many :room_users
- has_many :rooms, through: :room_users
- has_many :messages

## comments テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| room   | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :users

## message テーブル

| Column  | TYpe       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| users   | references | null: false, foreign_key: true |
| room    | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :users