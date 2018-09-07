# README

db design

## users table
|column|Type|Options|
|------|----|-------|
|last_name|string|null: false, unique: true|
|first_name|string|null: false, unique: true|
|email||(devise), null: false, unique: true|
|password||(devise), null: false|
|profile_img|string||
|review_id||foreign_key: true|

[association]
- has_many :reservations
- has_many :reviews
- has_many :messages


## reviews table
|column|Type|Options|
|------|----|-------|
|user_id|references|foreign_key: true|
|space_id|references|foreign_key: true|
|rate|integer||
|text|text||

association
- belongs_to :space


## hosts table
|column|Type|Options|
|------|----|-------|
|last_name|string|null: false|
|first_name|string|null: false|
|last_kana|string|null: false|
|first_kana|string|null: false|
|sex||null: false|
|year|integer|, null: false|
|month|integer|, null: false|
|day|integer|, null: false|
|profile_img|string||

[association]
- has_many :spaces


## spaces table
|column|Type|Options|
|------|----|-------|
|title|string|null: false|
|size||null: false|
|price_hour||null: false|
|price_day||null: false|
|capacity||null: false|
|post_num||null: false|
|prefecture||null: false|
|city||null: false|
|town||null: false|
|building||null: false|
|service|||
|image||null: false|
|use||null: false|
|review_id||null: false|
|host_id||null: false|
|key||null: false|
|period_reservation||null: false|
|plan_name||null: false|
|plan_description|||

association
- has_many :reservations
- belongs_to :host


## reservations table
|column|Type|Options|
|------|----|-------|
|date|string|null: false|
|time|integer|null: false|
|user_id|references|foreign_key: true|
|space_id|references|foreign_key: true|

association
- belongs_to :space
- belongs_to :user

## likes table
|column|Type|Options|
|------|----|-------|
|user_id|references|foreign_key: true|
|space_id|references|foreign_key: true|

association
- belongs_to :space
