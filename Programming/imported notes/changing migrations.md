Occasionally you will make a mistake when writing a migration. If you have already run the migration, then you cannot just edit the migration and run the migration again: Rails thinks it has already run the migration and so will do nothing when you run bin/rails db:migrate. You must rollback the migration (for example with bin/rails db:rollback), edit your migration, and then run bin/rails db:migrate to run the corrected version.

In general, editing existing migrations is not a good idea. You will be creating extra work for yourself and your co-workers and cause major headaches if the existing version of the migration has already been run on production machines.

Instead, you should write a new migration that performs the changes you require. Editing a freshly generated migration that has not yet been committed to source control (or, more generally, which has not been propagated beyond your development machine) is relatively harmless.

The revert method can be helpful when writing a new migration to undo previous migrations in whole or in part (see Reverting Previous Migrations above).