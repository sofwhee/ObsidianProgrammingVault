bin/rails db:migrate:status

If you run the bin/rails db:migrate:status command, which displays the status (up or down) of each migration, you should see ********** NO FILE ********** displayed next to any deleted migration file which was once executed on a specific environment but can no longer be found in the db/migrate/ directory.