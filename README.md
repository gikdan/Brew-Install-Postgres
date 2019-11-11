# Installing Postgres via Brew

## Pre-Reqs
[Brew Package Manager](http://brew.sh)

In your command-line run the following commands:

1. `brew doctor`
1. `brew update`

## Installing
1. In your command-line run the command: `brew install postgresql`
2. Run the command: `ln -sfv /usr/local/opt/postgresql/*.plist ~/Library/LaunchAgents`
3. Create two new aliases to start and stop your postgres server. They could look something like this:

     ```
     alias pg_start="launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist"
     alias pg_stop="launchctl unload ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist"
     ```

4. Run the alias you just created: `pg_start`. Use this comment to start your database service.
     - alternatively, `pg_stop` stops your database service.
5. Run the command: ``createdb `whoami` ``
6. Connect to your postgres with the command: `psql`
7. `brew reinstall readline` - **if needed**
8. `createuser -s postgres` - fixes `role "postgres" does not exist`
9. Test with `psql` command

     
     ```
      $ psql
     psql (11.3, server 11.5)
     Type "help" for help.

     danielmboya=#

      ```

## Commands

### Create database
```
createdb <database_name>
```
> `createdb myspring_postgres_project`

### List databases
```
psql -U postgres -l
```

### Show tables in database
```
psql -U postgres -d <database_name>
```
> `psql -U postgres -d myspring_postgres_project`

### Drop database
```
dropdb <database_name>
```
> `dropdb myspring_postgres_project`

### Restart database
```
dropdb <database_name> && createdb <database_name>
```
> `dropdb myspring_postgres_project && createdb myspring_postgres_project`
