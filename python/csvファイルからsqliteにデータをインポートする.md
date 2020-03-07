# csvファイルからsqliteにデータをインポートする

csvファイルの用意

```csv
id,name
1,taro
2,jun
3,mike
```

csvからsqliteにデータを読み込ませる処理


```python
import csv
import sqlite3


conn = sqlite3.connect('{sqlite-file}')
curs = conn.cursor()
curs.execute(
    'CREATE TABLE {db-table-name}\
    (id INTEGER, name TEXT,\
    PRIMARY KEY(id))'
)

with open('{csv-file}', 'r') as csv_file:
    render = csv.DictReader(csv_file)
    to_db = [
        (row['id'], row['name']) for row in render
    ]
    print(to_db)

curs.executemany('INSERT INTO {db-table-name}(id, name) VALUES (?, ?);', to_db)
conn.commit()
conn.close()
```
