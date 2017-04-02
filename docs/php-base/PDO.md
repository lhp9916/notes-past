# PDO 

[文档地址](http://php.net/manual/zh/intro.pdo.php)

### 连接
```php
try {
    $dbh = new PDO('mysql:host=localhost;dbname=test', $user, $pass);
    foreach($dbh->query('SELECT * from FOO') as $row) {
        print_r($row);
    }
    $dbh = null;
} catch (PDOException $e) {
    print "Error!: " . $e->getMessage() . "<br/>";
    die();
}
// 现在运行完成，在此关闭连接
$dbh = null;
```
要想关闭连接，需要销毁对象以确保所有剩余到它的引用都被删除，可以赋一个 NULL 值给对象变量。如果不明确地这么做，PHP 在脚本结束时会自动关闭连接。

### 事务
```php
try {  
  $dbh->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

  $dbh->beginTransaction();
  $dbh->exec("insert into staff (id, first, last) values (23, 'Joe', 'Bloggs')");
  $dbh->exec("insert into salarychange (id, amount, changedate) 
      values (23, 50000, NOW())");
  $dbh->commit();
  
} catch (Exception $e) {
  $dbh->rollBack();
  echo "Failed: " . $e->getMessage();
}
```

### 预处理语句
```php
$stmt = $dbh->prepare("INSERT INTO REGISTRY (name, value) VALUES (:name, :value)");
$stmt->bindParam(':name', $name);
$stmt->bindParam(':value', $value);

// ? 占位符
//$stmt = $dbh->prepare("INSERT INTO REGISTRY (name, value) VALUES (?, ?)");
//$stmt->bindParam(1, $name);
//$stmt->bindParam(2, $value);

// 插入一行
$name = 'one';
$value = 1;
$stmt->execute();

//  用不同的值插入另一行
$name = 'two';
$value = 2;
$stmt->execute();

```
```php
// 占位符必须被用在整个值的位置
$stmt = $dbh->prepare("SELECT * FROM REGISTRY where name LIKE ?");
$stmt->execute(array("%$_GET[name]%"));
```

### 存储过程 
```php
//带输出参数调用存储过程
$stmt = $dbh->prepare("CALL sp_returns_string(?)");
$stmt->bindParam(1, $return_value, PDO::PARAM_STR, 4000); 

//带输入/输出参数调用存储过程
$stmt = $dbh->prepare("CALL sp_takes_string_returns_string(?)");
$value = 'hello';
$stmt->bindParam(1, $value, PDO::PARAM_STR|PDO::PARAM_INPUT_OUTPUT, 4000);

// 调用存储过程
$stmt->execute();
```