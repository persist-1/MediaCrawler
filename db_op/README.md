# 数据库操作模块 (db_op)

本目录包含MediaCrawler项目的所有数据库操作相关模块。

## 模块说明

### async_db.py
- **功能**: 异步MySQL数据库操作封装
- **主要类**: `AsyncMysqlDB`
- **用途**: 提供MySQL数据库的增删改查操作

### async_sqlite_db.py
- **功能**: 异步SQLite数据库操作封装
- **主要类**: `AsyncSqliteDB`
- **用途**: 提供SQLite数据库的增删改查操作

## 使用方式

```python
# 导入数据库操作类
from db_op import AsyncMysqlDB, AsyncSqliteDB

# 或者单独导入
from db_op.async_db import AsyncMysqlDB
from db_op.async_sqlite_db import AsyncSqliteDB
```

## 配置说明

数据库模块的路径配置在 `config/db_config.py` 中定义：

```python
# 数据库操作模块路径配置
DB_OP_MODULE_PATH = "db_op"
ASYNC_DB_MODULE = f"{DB_OP_MODULE_PATH}.async_db"
ASYNC_SQLITE_DB_MODULE = f"{DB_OP_MODULE_PATH}.async_sqlite_db"
```
请优先引用 `db_op` 模块，不要直接引用 `async_db` 或 `async_sqlite_db` 模块，以提高维护性和可扩展性。

## 目录结构

```
db_op/
├── __init__.py          # 包初始化文件，导出主要类
├── async_db.py          # MySQL异步数据库操作
├── async_sqlite_db.py   # SQLite异步数据库操作
└── README.md           # 本说明文档
```

## 注意事项

1. 所有数据库操作都是异步的，需要在异步环境中使用
2. 使用前需要先初始化数据库连接
3. 建议通过 `db.py` 模块进行数据库初始化和管理
4. 新增数据库操作模块时，请在 `__init__.py` 中添加相应的导出