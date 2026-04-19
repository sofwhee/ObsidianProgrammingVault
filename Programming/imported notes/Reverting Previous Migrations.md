rails db:rollback

require_relative "20121212123456_example_migration"

class FixupExampleMigration < ActiveRecord::Migration[7.1]
  def change
    revert ExampleMigration

    create_table(:apples) do |t|
      t.string :variety
    end
  end
end

The revert method also accepts a block of instructions to reverse. 
This could be useful to revert selected parts of previous migrations.

For example, let's imagine that ExampleMigration is committed 
and it is later decided that a Distributors view is no longer needed.

class DontUseDistributorsViewMigration < ActiveRecord::Migration[7.1]
  def change
    revert do
      # copy-pasted code from ExampleMigration
      reversible do |direction|
        direction.up do
          # create a distributors view
          execute <<-SQL
            CREATE VIEW distributors_view AS
            SELECT id, zipcode
            FROM distributors;
          SQL
        end
        direction.down do
          execute <<-SQL
            DROP VIEW distributors_view;
          SQL
        end
      end

      # The rest of the migration was ok
    end
  end
end

The same migration could also have been written without using revert but this would have involved a few more steps:

Reverse the order of create_table and reversible.
Replace create_table with drop_table.
Finally, replace up with down and vice-versa.
This is all taken care of by revert.