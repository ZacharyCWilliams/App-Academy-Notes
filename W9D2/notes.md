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

NOTE: dependent: :destroy will handle child records. It will not handle our widowed foreign keys.

We need to add a **foreign key constraint at the database level** in order to maintain referential integrity (We do not want widowed foreign keys lying around)

