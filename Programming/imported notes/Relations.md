-- Looks like an Array --

User.where(id: 1) 
  # => [#<User id: 1, email: "foo@bar.com">] 

                      ^^^^
This is actually an instance of ActiveRecord::Relation.
It is NOT an Array.

(it's more efficient cause it doesn't actually run a query)
(run .to_a if you really want an array)

-- Chaining queries --

Post.limit(5).order(created_at: :desc)

#limit -> returns a Relation
#order -> adds its own criteria

Chain a dozen methods...

When it's time to execute, ActiveRecord and SQL
  will figure out the optimal way to structure the
  query.

-- These do NOT return Relations --

ActiveRecord::FinderMethods
.find
.find_by
.first
.last
.take
... etc

