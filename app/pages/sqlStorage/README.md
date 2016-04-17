# SqlStorage

SqlStorage采用SQLite查询。在文件系统中持久的储存数据，这是首选的储存引擎。引擎支持简单的键值对存储和完整的Sql查询。

```
let storage = new Storage(SqlStorage, options);
storage.set('name', 'Max');
storage.get('name').then((name) => {
});

// Sql storage also exposes the full engine underneath
storage.query('insert into projects(name, data) values("Cool Project", "blah")');
storage.query('select * from projects').then((resp) => {})

```

## 静态方法

### `BACKUP_LOCAL()`
### `BACKUP_LIBRARY()`
### `BACKUP_DOCUMENTS()`

## 实例方法


### `query(query,params)`

在数据库中执行SQL操作。

- query `string`

	sql字符串

- params `array`

返回一个`Promise`

### `get(key)`

从数据库中获取给定的键名所对应的键值。

返回一个`Promise`

### `set(key,value)`
从数据库中插入键值对

返回一个`Promise`
### `remove(key)`

从数据库中删除键值对。

返回一个`Promise`

### `clear()`

清空数据库