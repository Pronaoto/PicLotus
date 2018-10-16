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
|text|string|null: false|
|image|string|null: false|
|user_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user
- has_many: comments
- has_many: likes

## comments テーブル
|column|type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|post_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :post

## users テーブル
|column|type|Options|
|------|----|-------|
|nickname|string|null: false,unique: true|
|email|string|null: false,unique: true|
|avatar|string|

### Association
- has_many :posts
- has_many :comments
- has_many :relationships

## likes テーブル
|column|type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|post_id|references|null: false, foreign_key: true|

### Association
- belongs_to :posts

## relationshipsテーブル
|Column|Type|Options|
|------|----|-------|
|follower_id|integer|add_index :relationships, :follower_id|
|following_id|integer|add_index :relationships, :following_id|

### Association
- belongs_to :follower, class_name: "User"
- belongs_to :following, class_name: "User"
- validates :follower_id, presence: true
- validates :following_id, presence: true
