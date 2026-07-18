
Atomicity Consistency Isolation Durability

Atomicity -> Either all or None

For example we have a transaction T1

T1 (Read(A), A=A, Write(A),Read(B))

Note Transaction T1 has 4 operation if 1 operation failed then then we will roll back T1 transaction

Imp (A failed Transaction can not be resumed it will always restart)



