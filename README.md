# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

* DB-design
## usersテーブル

|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|username|string|null: false|
### Association
- has_many :group
- has_many :message


## groupテーブル

|Column|Type|Options|
|------|----|-------|
|groupname|stirng|null: false|
|chatmember|string|foreign_key: true|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- has_many :message
- has_many :users, throuth: :group_users


## group_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group


## messageテーブル

|Column|Type|Options|
|------|----|-------|
|image|string||
|message|text|null: false|
|created_at|datetime|null: false|
|updated_at|datetime|null: false|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group