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

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|content|string|    |
|image |string|     |
|user  |references|null: false, foreign_key: true|
|group |references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name  |string|null: false, index: true|
|e_mail|string|null: false|
|password|string|null: false|

### Association
- has_many :messages
- has_many :groups_users
- has_many :groups, thorugh: :groups_users

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name  |string|null: false|     

### Association
- has_many :messages
- has_many :gruop_users
- has_many :users, through: :gruop_users

## ## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user  |references|null: false, foreign_key: true|
|group |references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user