# Rails API Relationships Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  Describe a reason why a join tables may be valuable.

  ```md
    I can create new features that will be useful for both tables and also not expensive in terms of database processing. For example table Books can have many Borrowers and Borrowers can have many Books and with join table we can create two directions of data flow in one new table - join table.
  ```

1.  Provide a database table structure and explain the Entity Relationship that
  describes a many-to-many relationship for `Profiles`, `Movies` and `Favorites`
  (Think of Netflix). A `Profile` has a `given_name`, `surname` and `email` and a
  `Movies` have `title`, `release_date`, and `length` and `Favorites` would be the
  join table with references to `Movies` and `Profiles`.

  ```md
  class Profiles < ActiveRecord
  has_many :movies

  validates :name, presence: true
  validates :password, presence: true

  end

  class Movies < ActiveRecord
    belongs_to :profile :favorite
    has_many :profiles

    validates :title, presence: true
    validates :length, presence: true
    validates :genre, presence: true
  end

  class Favorites < ActiveRecord


  end
  ```

1.  For the above example, what needs to be added to the Model files?

  ```rb
  class Profile < ActiveRecord::Base
  end
  ```

  ```rb
  class Movie < ActiveRecord::Base
  end
  ```

  ```rb
  class Favorite < ActiveRecord::Base
  end
  ```

1.  What is the purpose of a serializer? What would our `Profile` serializer look
like to show all movies favorited by a profile on
`http://localhost:3000/profiles/1`

  ```md
    Gives columns in the certain order.
  ```

  ```rb
  class ProfileSerializer < ActiveModel::Serializer
  end
  ```

1.  What would the command be to _scaffold_ out a **join table** for Favorites from
the above `Movies` and `Profiles`.

  ```sh
    # < Your Response Here >
  ```

1.  What is `Dependent: Destroy` and where/why would we use it?

  ```md
    If we delete one we proably want to delete the association with the other. Rails helps us with this with a method called depend destroy
  ```

1.  Think of **ANY** example where you would have a one-to-many relationship as well
as a many-to-many relationship in an application. You only need to list the
description about the resources and how they relate to one another.

  ```md
  many-to-many   - public library - books have many borrowers (in different time)
  borrowers can borrow many books - a book has_many :borrowers belongs_to :borrower
  and borrower has_many :books belongs_to :book

  one-to-many - a dog has many dogsitters - has_many :dogsitters  belongs_to :dogsitter
  ```
