
Atomicity Consistency Isolation Durability

Atomicity -> Either all or None

For example we have a transaction T1

T1 (Read(A), A=A, Write(A),Read(B))

Note Transaction T1 has 4 operation if 1 operation failed then then we will roll back T1 transaction

Imp (A failed Transaction can not be resumed it will always restart)


Consistency -> Before transaction start and after the transaction end the Sum of total money must be same

Isolation ->To convert peraler schedute to serial schedule because serial schedule will always be consitant conflict serializability view serializability

Durability -> Successful transaction will always be persist

===============================================================

States of Transaction 

Active State (Ex When we load Data or program in R.A.M)

Partially Committed (All operation are Done in a Transaction except commit Means "n-1 operations are Done")

Committed -> All n operation are Done and save in Hard Disk also 

Terminated -> Release all the resources like free up the ram and memory and C.P.U

Failed -> A Transaction will always be failed in Active or Partially committed State And we move it to Abort State

Abort State -> Will mark as Fail or Restart the transaction






