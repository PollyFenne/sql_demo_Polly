### Study Notes

[SQL](https://github.com/getfutureproof/fp_guides_wiki/wiki/SQL)

Pull progres image and creating container called shelter-db in the folder called code
`docker run --name shelter-db --mount type=bind,source="$(pwd)",dst="/code" -e POSTGRES_PASSWORD=password -d postgres`

Open up and go into container
`docker exec -it shelter-db psql -U postgres`

Show a list of possible commands
`/h`

Show more detail of specific command
`/h <command name>`

List all toables
`/dt`

Create a table:
```
postgres=# CREATE TABLE cats (
postgres(# id serial PRIMARY KEY,
postgres(# name VARCHAR (20) NOT NULL,
postgres(# age INT
postgres(# );
```
The serial command, will auto increment the ID

The above can be written all on one line. The above command will create a table which looks like:
```
postgres=# \dt
        List of relations
 Schema | Name | Type  |  Owner
--------+------+-------+----------
 public | cats | table | postgres
(1 row)
```

Adding data to the table
```
postgres=# INSERT INTO cats (name, age)
postgres-# VALUES
postgres-# ('Zelda', 9),
postgres-# ('Truffle', 1);
```

Run database
`\i code/setup.sql`


`DISTINCT` command will fetch variables that are unique

Inner join
```
postgres=# SELECT cats.name, breeds.name FROM cats INNER JOIN breeds ON cats.breed_id = breeds.id;
   name    |       name
-----------+-------------------
 Zelda     | American Wirehair
 Tigerlily | Persian
 Sam       | Siamese
 Salem     | British Longhair
 Fluffy    | American Wirehair
 Didi      | Persian
(6 rows)
```

Left join:
```
postgres=# SELECT cats.name, breeds.name FROM cats LEFT JOIN breeds ON cats.breed_id = breeds.id;
   name    |       name        
-----------+-------------------
 Zelda     | American Wirehair 
 Tigerlily | Persian
 Sam       | Siamese
 Albus     |
 Leo       |
 Salem     | British Longhair
 Fluffy    | American Wirehair
 Didi      | Persian
 Bastian   |
 Kellog    |
 ```
 
 The data bases are now linked as follows: 
 ![image](https://user-images.githubusercontent.com/113044818/204512708-723171ab-61ec-4a1d-b055-32850da79fb6.png)

