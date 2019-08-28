# W9D2 - Controllers Continued

## Relational Callbacks 

Methods we call at certain points within the active record objects lifecycle (ie. create, update, destroy, etc.)

**Example:**
```
class User < ApplicationRecord
  has_many :posts, dependent: :destroy
end

class Post < ApplicationRecord
  belongs_to :user
end
```
We use the relational callback `dependent: :destroy` so that if a user is destroyed
that users posts will also be destroyed. We generally use this on the `has_many` association. Not the `belongs_to`

## Active Record and Referential Integrity

NOTE: `dependent: :destroy` will handle child records. It will not handle our widowed foreign keys.

We need to add a **foreign key constraint at the database level** in order to maintain referential integrity (We do not want widowed foreign keys lying around)

## Domain Name System (DNS)

Translates domain names to IP addresses 

Example:

`www.google.com` translates to `8.8.8.8` and `8.8.4.4`

* DNS has a distributed directory service 
* DNS servers hold information
* DNS resolvers look up information

## Querying for a domain server

1. Query moves from DNS resolver to DNS server
2. If server doesn't need to look up additional info it will return result
3. If server needs to look up additional info it will either:
  3. Change it's role and become the information searcher. It will then pass the information to another name server (This is done recursively)
  3. Return it's best guess as to what other name server might have the information. It will then return that name servers IP address to the original resolver so that it can search through that server. (This is done iteratively)

## A security risk: Cache Poisioning

Attacker replaces valid cache entries with corrupted data (usually a redirect to their site)

Consider the following example: 

1. You want to go to bankofamerica.com
2. They send you to bankofusa.com 
3. You put in your banking login info and now the attacker has access to your account

## Building A JSON API




