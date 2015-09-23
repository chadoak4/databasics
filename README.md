## Databasics

<!---
  HOMEWORK QUESTIONS
  1.Time Stamp?
  2.Expand column width?
-->

Fork this repository into your own github profile.

Before closing the homework assignment issue:

- Update this README as follows:
  - [x] For each question (just after or below the question itself) include the SQL you wrote to generate the answer
  - [x] For each question (just after or below the question itself) include the *answer* to the question asked.

- Also:
  - [x ] Commit the updated `store.sqlite3` database file
  - [x] Include a link to your forked repo in the comments when closing the issue.


NOTE: To run sqlite with this database: `sqlite3 store.sqlite3`

NOTE: You may want to keep a backup of the `store.sqlite3` file in case you damage the file. *OR* you can use the command `git checkout store.sqlite3` to undo any changes to the database file since the fork or your last commit.

## Explorer Mode

- [x] How many users are there?
  ```SELECT COUNT(id) from users; 50```
- [x] What are the 5 most expensive items?
  ```SELECT * FROM items ORDER BY price DESC LIMIT 5;
        25          Small Cotton Gloves  Automotive, Shoes & Beauty  Multi-layered modular service-desk  9984
        83          Small Wooden Comput  Health                      Re-engineered fault-tolerant adapt  9859
        100         Awesome Granite Pan  Toys & Books                Upgradable 24/7 access              9790
        40          Sleek Wooden Hat     Music & Baby                Quality-focused heuristic info-med  9390
        60          Ergonomic Steel Car  Books & Outdoors            Enterprise-wide secondary firmware  9341```
- [x] What's the cheapest book? (Does that change for "category is exactly 'book'" versus "category contains 'book'"?)
      ```SELECT title, min(price) FROM ITEMS WHERE category="Books";
          Ergonomic Granite Chair  1496
        SELECT title, min(price) FROM items WHERE category LIKE "Books";
          Ergonomic Granite Chair  1496```

- [x] Who lives at "6439 Zetta Hills, Willmouth, WY"? Do they have another address?
        ```SELECT "first_name", "last_name", "street", "city", "state", "zip" FROM "users" AS U JOIN "addresses" AS A ON U.id=user_id WHERE STREET LIKE  "6439 ZETTA HILLS";
          Corrine     Little      6439 Zetta Hills  Willmouth   WY          15029
        SELECT "first_name", "last_name", "street", "city", "state", "zip" FROM "users" AS U JOIN "addresses" AS A ON       U.id=user_id WHERE first_name LIKE  "Corrine";
          Yes. She has a second address : 54369 Wolff Forg  Lake Bryon  CA          31587```
- [x] Correct Virginie Mitchell's address to "New York, NY, 10108".
    ```UPDATE addresses SET city = "New York", zip = 10108 WHERE zip = "31587"
       UPDATE addresses SET city = "New York", zip = 10108 WHERE zip = "15029"```

- [x] How much would it cost to buy one of each tool?
        ```SELECT sum(price) FROM ITEMS WHERE category LIKe '%Tool%';
          46477```
- [x] How many total items did we sell?
      ```SELECT  sum(quantity) FROM orders;
          2125```
- [x] How much was spent on books?
      ```SELECT SUM(price*quantity) FROM items INNER JOIN orders ON items.id - orders.item_id WHERE items.category LIKE "%Books%";
        124805773```

- [x] Simulate buying an item by inserting a User for yourself and an Order for that User.
        ```INSERT INTO users VALUES ("51", "Chad", "Oakley", "Chad.Oakley@tampabay.rr.com");
        INSERT INTO orders VALUES ("378", "51", "4", "1",CURRENT_TIMESTAMP);
          51          Chad        Oakley      Chad.Oakley@tampabay.rr.co
          378         51          4           1           2015-09-23 05:01:56```


## Adventure Mode

- [ ] What item was ordered most often? Grossed the most money?
- [ ] What user spent the most?
- [ ] What were the top 3 highest grossing categories?
