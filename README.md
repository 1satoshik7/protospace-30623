# テーブル設計

## users table

| Colum      | Type   | Options     |
| ---------- | ------ | ----------- |
| email      | string | null: false |
| password   | string | null: false |
| name       | string | null: false |
| profile    | text   | null: false |
| occupation | text   | null: false |
| position   | text   | null: false |

### Association

- has_many :prototypes
- has_many :comments

## prototypes table

| Colum      | Type       | Options           |
| ---------- | ---------- | ----------------- |
| title      | string     | null: false       |
| catch_copy | text       | null: false       |
| concept    | text       | null: false       |
| image      |            |                   |
| user       | references | foreign_key: true |

### image は ActiveStorage で実装
### Association

- belongs_to :user
- has_many :comments

## comments table

| Colum           | Type       | Options           |
| --------------- | ---------- | ----------------- |
| text            | text       | null: false       |
| user            | references | foreign_key: true |
| prototype       | references | foreign_key: true |

### Association

- belongs_to :prototype
- belongs_to :user