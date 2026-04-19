bin/rails generate migration MigrationName

bin/rails generate model User name:string password:string
  =     create_table :products do |t|
          t.string :name
          t.text :description

          t.timestamps

bin/rails generate controller PluralizedName [list of actions] [list of --options]

bin/rails generate controller Cowards index show

bin/rails generate migration AddColumnToTable part_number:string
  =    add_column: :users, :part_number, :string (...)

bin/rails generate migration AddColumnToTable part_number:string:index
  =    add_column: :users, :part_number, :string
       add_index :products, :part_number (...)

bin/rails generate migration AddColumnToTable part_number:string price:decimal
  =     add_column :products, :part_number, :string
        add_column :products, :price, :decimal

bin/rails generate migration RemoveColumnFromTable part_number:string
  =     remove_column :products, :part_number, :string

bin/rails generate migration CreateProducts name:string part_number:string
  =     create_table :products do |t|
            t.string :name
            t.string :part_number

            t.timestamps  

bin/rails generate migration AddUserRefToProducts user:references
  =    add_reference :products, :user, foreign_key: true
(also available as belongs_to)

bin/rails generate migration CreateJoinTableCustomerProduct customer product
  =    create_join_table :customers, :products do |t|
          # t.index [:customer_id, :product_id]
          # t.index [:product_id, :customer_id]

bin/rails generate migration AddDetailsToProducts 'price:decimal{5,2}' supplier:references{polymorphic}
  =    add_column :products, :price, :decimal, precision: 5, scale: 2
       add_reference :products, :supplier, polymorphic: true

---
change_table :products do |t|
  t.remove :description, :name
  t.string :part_number
  t.index :part_number
  t.rename :upccode, :upc_code
end

change_column :products, :part_number, :text
change_column_null :products, :name, false
change_column_default :products, :approved, from: true, to: false

comment 
  Adds a comment for the column.
collation 
  Specifies the collation for a string or text column.
default 
  Allows to set a default value on the column. 
  Note that if you are using a dynamic value (such as a date), 
  the default will only be calculated the first time 
  (i.e. on the date the migration is applied). 
  Use nil for NULL.
limit 
  Sets the maximum number of characters for a string column 
  and the maximum number of bytes for text/binary/integer columns.
null 
  Allows or disallows NULL values in the column.
precision 
  Specifies the precision for decimal/numeric/datetime/time columns.
scale 
  Specifies the scale for the decimal and numeric columns, representing the number of digits after the decimal point.