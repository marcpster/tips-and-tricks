# Postgres

## Timezones

Default timezone is typically `Etc/UTC`. Change timezone for a session e.g.

  ```sql
  SET timezone TO 'Europe/London';
  -- etc
  ```
## Queries
Querying JSON columns. The short arrow -> keeps the type as JSON, and the long arrow ->> returns text.

  ```sql
  SELECT * from logs WHERE loginfo->>'row.id' = '0'
  SELECT * FROM logs WHERE (loginfo->>'logtitle')::text ilike '%send%'
  SELECT js->0 FROM events --index of a JSON array
  ```

## Quick Backup

Even if your DB is backed up regularly, a quick backup to CSV is also useful.

The example below backs up some tables to a folder on the PG server.

  ```sql
    COPY (SELECT * FROM user_store) TO '/slgt-export/users.csv' CSV HEADER;
    COPY (SELECT * FROM users_ext) TO '/slgt-export/ext.csv' CSV HEADER;
  ```

## Grants

Check the column grants 
  ```sql
  SELECT * FROM information_schema.role_column_grants
    WHERE table_name='user_store' and column_name='mail' limit 10;
  ```

## Random Selections
Useful for sampling data - this can be slow on a large table.
  ```sql
  SELECT * FROM user_store ORDER BY RANDOM() LIMIT 50;
  ```

## UPDATE join

  ```sql
  UPDATE t1
  SET t1.c1 = new_value
  FROM t2
  WHERE t1.c2 = t2.c2
  ```

## (Re) Create schema

  !!! This will drop all tables !!!
  ```sql
  drop schema public cascade;
  ```
  Create fresh schema
  ```sql
  create schema public;
  grant all on schema public to public;
  comment on schema public is 'standard public schema';
  ```

## PSQL
### Commands
 - `\conninfo` Show connection details (including user)
 - `\o {path}` Send all query results to file or |pipe. \o to switch off.

### Copy CSV to table

  ```sql
  CREATE TABLE IF NOT EXISTS admin.intercom (
     email varchar(128), user_id varchar(64));
  ```
  psql \copy admin.intercom FROM /mnt/c/tmp.csv WITH CSV
