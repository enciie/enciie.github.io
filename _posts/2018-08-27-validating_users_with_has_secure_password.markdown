---
layout: post
title:      "Validating Users with has_secure_password"
date:       2018-08-27 22:55:01 -0400
permalink:  validating_users_with_has_secure_password
---


`has_secure_password`  method comes from the ActiveModel::SecurePassword module that is automatically included in ActiveRecord::Base. This method gives our User model authentication methods to set and authenticate against a BCrypt password. You will need to make sure you add the BCrpyt gem to your Gemfile. And add the method to the User class as below:

```
class User < ActiveRecord::Base
    has_secure_password
end
```

ActiveRecord's `has_secure_password`  method requires you to have a `password_digest` attribute. So you will need a column `password_digest'` in your users migration table, instead of `password` for the User model's attribute. The attribute password is encrypted before being stored in your database. This is done by BCrypt gem. 

```
create_table "users", force: :cascade do |t|
    t.string   "username"
    t.string   "email"
    t.string   "password_digest"
    t.datetime "created_at",      null: false
    t.datetime "updated_at",      null: false
  end
```

BCrypt is an open source gem that hashes and adds "salt" to a password - these are two separate processes.  A salt is simply a random string of characters that gets added into the string. In other words, it disguises the plain text passwords and makes it difficult to decode it. The other process of hashing, encrypts the password and guards against the possibility that someone who gains unauthorized access to the database can retrieve the passwords of every user in the system.

Some of the methods that `has_secure_password` adds are `password=` and `authenticate`. 

** password=(unencrypted_password)** : Encrypts the password into the `password_digest` attribute, only if the new password is not empty. It takes the string from the user's input and encrypts and stores it in the `password_digest` attribute.

```
user = User.new
user.password = 'p@ssword'
user.password_digest # => "$2a$10$4LEA7r4YmNHtvlAvHhsYAeZmk/xeUVtMTYqwIvYY76EW5GUqDiP4."
```

** authenticate(unencrypted_password)** : Returns `self` if the password is correct, otherwise `false`. 

```
user = User.new(username: 'frank', password: 'p@ssword')
user.save
user.authenticate('wr0ngpassword') #=> false
user.authenticate('p@ssword') #=> user
```

1.  Takes a `string` as an argument from user's input
2.  It turns the `string` into a salted, hashed version 
3.  It compares this salted, hashed version with the user's stored `password_digest` in the database
4.  if the two versions are a match, `authenticate` method will return the `User` instance; if not, it returns `false`.
