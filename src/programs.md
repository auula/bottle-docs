### Follow-up maintenance 🎈

- `Bottle` does not currently support multi-data storage partitions, and subsequent versions will introduce a `Bucket` concept. In the future, the specified data can be stored in the specified partition to reduce the particle size of the lock when concurrent.

- Subsequent `zero copy` technology, the current file operation is largely dependent on the operating system, and the current file must be `SYNC` to ensure data consistency.

- Dirty data combination can be consolidated in operation, and the garbage collection work thread is notified based on the `signal`.