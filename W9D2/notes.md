W9D2 - Controllers Continued

Relational Callbacks 

Example:
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

Ac