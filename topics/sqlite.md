# SQLite

# Create a SQLite DB with C#
install Microsoft.EntityFrameworkCore.Tools

From Package Manager Console:
// creates migration files
add-migration {DBName}{migrationName} (Ex. CityInfoDBInitialMigration)

// creates .db file from migration
update-database