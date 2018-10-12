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

## posts テーブル
|column|type|Options|
|------|----|-------|
|text|string|null: false, unique: true, index: true|
|image|string|null: false|
|user_id|string|null: false|

### Association
- belongs_to :user
- has_many: comments
- has_many: likes

## messages table
|column|type|Options|
|------|----|-------|
|body|text|-------|
|image|string|-------|

### Association
- belongs_to :user
- belongs_to :group

## users table
|column|type|Options|
|------|----|-------|
|name|string|null: false,unique: true|
|email|string|null: false|

### Association
- has_many :members
- has_many :groups, through: :members
- has_many :messages

## groups table
|column|type|Options|
|------|----|-------|
|name|string|null: false,unique: true|

### Association
- has_many :members
- has_many :users, through: :members
- has_many :messages
