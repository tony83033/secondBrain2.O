This method write down a summary of the action to be performed into log before actually writing them to the disk . In the case of crash the OS or DB simple check this logs and pick up from where it left off.

DB and OS both use this in OS it's called Journaling and DB it's called WAP 

System that implement data journaling include Linux ext3 ,ext4 Windows NTFS

Database Using WAL

PostgresSQL Uses WAL extensively for crash recovery and replication
MySQL InnoDB uses a redo log based on write ahead logging principles
SQLLIte offers a WAL mode that improves concurrency.