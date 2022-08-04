# MySQL Password

  - 발생한 에러 
    
    ```
    (28000): Access denied for user ‘root’@‘localhost’ (using password: YES)
    ```

<br />

  - 해결 시도

     - mysql> UPDATE user set password=password(“1234”) where user = ‘root’;

     ```
      ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ’(“1234”) where user = ‘root” at line 1
     ```

   - 해결 

     1. mysql -u root -p

     2. alter user 'root'@'localhost' identified with mysql_native_password by 'my_new_password';

     3. flush privileges;

 
