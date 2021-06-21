# テーブル設計

## users テーブル

| Column              | Type    | Options                   |
| ------------------- | ------- | ------------------------- |
| nickname            | string  | null: false               |
| email               | string  | null: false, unique: true |
| encrypted_password  | string  | null: false               |
| last_name           | string  | null: false               |
| first_name          | string  | null: false               |
| birthday            | date    | null: false               |

### Association

- has_many :posts

##　posts テーブル

| Column             | Type       | Options           |
| ------------------ | ---------- | ----------------- |
| drink_name         | string     | null: false       |
| drink_info         | text       | null: false       |
| category_id        | integer    | null: false       |
| calorie            | integer    | null: false       |
| price              | integer    | null: false       |
| user               | references | foreign_key: true |

### Association

- belongs_to :user
- has_many :post_toppings

## toppings テーブル

| Column        | Type    | Options     |
| ------------- | ------- | ----------- |
| calorie       | integer | null: false |
| topping_name  | string  | null: false |
| price         | integer | null: false |

### Association

- has_many :post_toppings

## post_toppings テーブル

| Column  | Type       | Options           |
| ------- | ---------- | ----------------- |
| post    | references | foreign_key: true |
| topping | references | foreign_key: true |

- belongs_to :post
- belongs_to :topping