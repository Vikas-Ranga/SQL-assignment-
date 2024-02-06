# SQL-assignment- 
**Query 1) What is the total number of blocks**
```SQL
SELECT COUNT(*) AS total_blocks
FROM bigquery-public-data.crypto_bitcoin.blocks;
```
![image](https://github.com/Vikas-Ranga/SQL-assignment-/assets/154298566/f7c4aeeb-05fb-485b-89b0-c4bf62c83cf3)

 
**Query 2) list out the average block size**
```SQL
SELECT AVG(size) AS avg_size
FROM bigquery-public-data.crypto_bitcoin.blocks
```
![image](https://github.com/Vikas-Ranga/SQL-assignment-/assets/154298566/ad60b307-81df-4cf6-a9f1-470e96dc7151)


 
**Query 3)Name the Block which has the most number of transactions**
```SQL
SELECT *
FROM `bigquery-public-data.crypto_bitcoin.blocks`
ORDER BY transaction_count DESC
LIMIT 1;
```
 ![image](https://github.com/Vikas-Ranga/SQL-assignment-/assets/154298566/598d23a0-7b4b-4db6-999d-0fe23109ef18)


 

**Query 4)Name the blocks which has the block size greater than 100000**
```SQL
SELECT *
FROM `bigquery-public-data.crypto_bitcoin.blocks`
WHERE size > 1000000;
```
![image](https://github.com/Vikas-Ranga/SQL-assignment-/assets/154298566/acb1da5e-0193-40e5-9aa1-8b018d5d3402)


 


**Query 5) How many Bitcoin transactions occurred on January 1, 2023?**
```SQL
SELECT COUNT(*) AS transactions_on_january_1_2023
FROM `bigquery-public-data.crypto_bitcoin.transactions`
WHERE DATE(block_timestamp) = '2023-01-01';
```
![image](https://github.com/Vikas-Ranga/SQL-assignment-/assets/154298566/51ebf5fe-2491-4918-b975-6c8a35daa19e)


 

**Query 6)What is the average transaction size in bytes for Bitcoin transactions?**
```SQL
SELECT AVG(size) AS average_transaction_size_bytes
FROM `bigquery-public-data.crypto_bitcoin.transactions`;
```
![image](https://github.com/Vikas-Ranga/SQL-assignment-/assets/154298566/36570894-b30b-49e5-a15d-c12c402ce874)


 


**Query 7) How many distinct Bitcoin block IDs are there in the dataset?**
```SQL
SELECT COUNT(DISTINCT block_hash) AS distinct_block_ids
FROM `bigquery-public-data.crypto_bitcoin.transactions`;
```
![image](https://github.com/Vikas-Ranga/SQL-assignment-/assets/154298566/820ba585-fe83-4846-9197-1b7936207770)

**Query 8) 1.	WHAT IS THE NO.OF TRANSACTION COUNT AS PER THE BLOCKS?**
```SQL
SELECT
  block_hash,
  COUNT(*) AS transaction_count
FROM
  `bigquery-public-data.crypto_bitcoin.blocks` AS blocks
JOIN
  `bigquery-public-data.crypto_bitcoin.transactions` AS transactions
ON
  blocks.hash = transactions.block_hash
GROUP BY
  block_hash
ORDER BY
  transaction_count DESC;
LIMIT 5
```
![image](https://github.com/Vikas-Ranga/SQL-assignment-/assets/154298566/0890b344-c908-4f93-9146-91892b01dd1d)



**Query9) WHAT IS THE AVERAGE TRANSACTION FEE ACCORDING TO PER BLOCK?**
```SQL
SELECT
  block_hash,
  AVG(fee) AS average_fee
FROM
  `bigquery-public-data.crypto_bitcoin.blocks` AS blocks
JOIN
  `bigquery-public-data.crypto_bitcoin.transactions` AS transactions
ON
  blocks.hash = transactions.block_hash
GROUP BY
  block_hash
ORDER BY
  average_fee DESC;
```
![image](https://github.com/Vikas-Ranga/SQL-assignment-/assets/154298566/85628bb2-ba8e-49f3-99ed-3fa0707ba222)



**Query 10)What are the blocks with highest transaction fees?**
```SQL
SELECT
  blocks.hash,
  SUM(transactions.fee) AS total_fee
FROM
  `bigquery-public-data.crypto_bitcoin.blocks` AS blocks
JOIN
  `bigquery-public-data.crypto_bitcoin.transactions` AS transactions
ON
  blocks.hash = transactions.block_hash
GROUP BY
  blocks.hash
ORDER BY
  total_fee DESC
LIMIT 5;
```
![image](https://github.com/Vikas-Ranga/SQL-assignment-/assets/154298566/bfeacc47-87b6-4d78-bbf4-817a6a24a1c2)








