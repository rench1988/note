#### 搜索慢查询
```console
SELECT pid, now() - pg_stat_activity.query_start AS duration, query, state FROM pg_stat_activity WHERE (now() - pg_stat_activity.query_start) > interval '5 seconds';
```

#### where like语句
```console
select * from pg_stat_activity where query LIKE '%' || 'SELECT UploadSwapFile' || '%';
```

