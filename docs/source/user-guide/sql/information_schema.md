

# Information Schema

DataFusion supports showing metadata about the tables and views available. This information can be accessed using the
views of the ISO SQL `information_schema` schema or the DataFusion specific `SHOW TABLES` and `SHOW COLUMNS` commands.

To show tables in the DataFusion catalog, use the `SHOW TABLES` command or the `information_schema.tables` view:

```sql
> show tables;
or
> select * from information_schema.tables;
+---------------+--------------------+------------+------------+
| table_catalog | table_schema       | table_name | table_type |
+---------------+--------------------+------------+------------+
| datafusion    | public             | t          | BASE TABLE |
| datafusion    | information_schema | tables     | VIEW       |
| datafusion    | information_schema | views      | VIEW       |
| datafusion    | information_schema | columns    | VIEW       |
+---------------+--------------------+------------+------------+

```

To show the schema of a table in DataFusion, use the `SHOW COLUMNS` command or the `information_schema.columns` view:

```sql
> show columns from t;
or
> select table_catalog, table_schema, table_name, column_name, data_type, is_nullable from information_schema.columns;
+---------------+--------------+------------+-------------+-----------+-------------+
| table_catalog | table_schema | table_name | column_name | data_type | is_nullable |
+---------------+--------------+------------+-------------+-----------+-------------+
| datafusion    | public       | t          | Int64(1)    | Int64     | NO          |
+---------------+--------------+------------+-------------+-----------+-------------+
```

To show the current session configuration options, use the `SHOW ALL` command or the `information_schema.df_settings` view:

```sql
select * from information_schema.df_settings;

+-------------------------------------------------+---------+
| name                                            | setting |
+-------------------------------------------------+---------+
| datafusion.execution.batch_size                 | 8192    |
| datafusion.execution.coalesce_batches           | true    |
| datafusion.execution.time_zone                  | UTC     |
| datafusion.explain.logical_plan_only            | false   |
| datafusion.explain.physical_plan_only           | false   |
| datafusion.optimizer.filter_null_join_keys      | false   |
| datafusion.optimizer.skip_failed_rules          | true    |
+-------------------------------------------------+---------+
```
