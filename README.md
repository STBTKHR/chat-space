# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

# DB設計
## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false,index: true|
|email|string|null: false,index: true,unique: true|
|password|string|null: false|

### Association
- has_many :groups_users
- hss_many :groups, through: :groups_users
- has_many :chats

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
- has_many :groups_users
- hss_many :users, through: :groups_users
- has_many :chats

## group_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## chatsテーブル

|Column|Type|Options|
|------|----|-------|
|content|string||
|image|string||
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
