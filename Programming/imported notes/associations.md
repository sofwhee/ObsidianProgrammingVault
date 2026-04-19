class User < ActiveRecord::Base
  has_many :posts
end

class Post < ActiveRecord::Base
  belongs_to :user
end

Post.first.user 
  -> Rails looks for a foreign key called user_id in the Posts table.
  -> Then it matches that user_id with an id in the Users table.
  -> Then it serves the User to you. 

Post.first.user -> if Posts.key?("user_id") -> id_from_posts = Posts.user_id.find(user.id) -> Users.find_by_id(id_from_posts)

belongs_to:
  This will create a "foreign key".
  It's just a column that SHOULD point to IDs in another table.
  Rails expects the name of this column to match with a table.
  The foreign key "user_id" should point to a User.id.
  If this isn't the case, you gotta tell Rails, buddy.