> 자동으로 증가하는 열 만들기

- 열(Column) 이름은 id, 데이터 타입은 정수(INT)로 만듬
- 데이터 타입 뒤에 AUTO_INCREMENT PRIMARY KEY를 붙임

```
MariaDB [test]> CREATE TABLE test (
                  id INT AUTO_INCREMENT PRIMARY KEY
                );
```

```
MariaDB [test]> DESCRIBE test;

+-------+---------+------+-----+---------+----------------+
| Field | Type    | Null | Key | Default | Extra          |
+-------+---------+------+-----+---------+----------------+
| id    | int(11) | NO   | PRI | NULL    | auto_increment |
+-------+---------+------+-----+---------+----------------+
```

👉 DESCRIBE : 테이블의 구조 보기

<br/><br/>

> 데이터 추가하기

- 데이터를 추가할 때 값을 지정하지 않아도 가능
- 1부터 값이 저장

```
MariaDB [test]> INSERT INTO test VALUES ();
```

```
MariaDB [test]> SELECT * FROM test;

+----+
| id |
+----+
|  1 |
+----+
```

- 다시 데이터를 추가하면 1보다 하나 큰 2가 됨

```
MariaDB [test]> INSERT INTO test VALUES ();
```

```
MariaDB [test]> SELECT * FROM test;

+----+
| id |
+----+
|  1 |
|  2 |
+----+
```

TIP.
MariaDB [test]> INSERT INTO test VALUES (123);

- 이후 값이 없는 행을 추가하면 id는 123 보다 하나 큰 124 추가

- 두번째 행을 지우기

```
MariaDB [test]> DELETE FROM test WHERE id = 2;
```

```
MariaDB [test]> SELECT * FROM test;

+----+
| id |
+----+
|  1 |
+----+
```

- 데이터를 추가하면 3이 값이 됨
- 즉, 삭제한 값을 다시 사용하지 않음

```
MariaDB [test]> INSERT INTO test VALUES ();
```

```
MariaDB [test]> SELECT * FROM test;

+----+
| id |
+----+
|  1 |
|  3 |
+----+
```

- 테이블의 모든 값을 삭제

```
MariaDB [test]> DELETE FROM test;
```

- 데이터 추가

```
MariaDB [test]> INSERT INTO test VALUES ();
```

- 이전에 사용한 값보다 큰 값부터 시작

```
MariaDB [test]> SELECT * FROM test;

+----+
| id |
+----+
|  4 |
+----+
```

<br/><br/>

> 초기화 하기

- 초기화 또는 시작하는 번호를 정하고 싶을 경우(1부터 시작)

```
MariaDB [test]> ALTER TABLE test AUTO_INCREMENT = 1;
```
