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


## users テーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null;false,index:true|

### Association
- has_many :group_users
- has_many :group, through: :group_users
- has_many :messages


## group_users テーブル
|Column|Type|Options|
|------|----|-------|
|user|references|null;false,foreign_key:true|
|group|references|null;false,foreign_key:true|

### Association
- belongs_to :group
- belongs_to :user


## groups テーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null;false,index:true|

### Association
- has_many :group_users
- has_many :user, through: :group_users
- has_many :messages


## messages テーブル
|Column|Type|Options|
|------|----|-------|
|text|text|-------|
|user|references|null;false,foreign_key:true|
|group|references|null;false,foreign_key:true|

### Association
- belongs_to :group
- belongs_to :user