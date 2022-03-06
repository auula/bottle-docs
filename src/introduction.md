### What is Bottle🤔?

> 👨🏻‍💻: Bottle is a lightweight kv storage engine based on LSM-TREE.

### Project Introduction

The first thing to note is that Bottle is a KV embedded storage engine, not a KV database. I know that many people see KV and think it is a database, but of course not. Many people will confuse these, KV storage can be used to store a lot of things, not the realm of databases. It can be understood that the database is a car, then the Bottle is the engine of a car. It can be simply understood that Bottle is an abstract KV encapsulation of the operating system file system. Based on Bottle as the storage layer, a database can be implemented by encapsulating some data structures and external service protocols on the Bottle layer.

![hierarchy](https://tva1.sinaimg.cn/large/e6c9d24egy1gzfrmt7qo4j21c20u0tai.jpg)


> The function implementation of this project is completely based on the [`bitcask`](https://blog.ibyte.me/post/bitcask-kvbase/) paper. 

Interested friends can go and see this course. If you think it is good, you can give me a small star ⭐ Thank you.