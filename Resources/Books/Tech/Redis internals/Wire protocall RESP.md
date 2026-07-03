resp is a array of string

Redis use RESP as a request response protocol
it support int , string array char, in RESP every datatype start with a special character and the data end with \r \n CRLF (Carriage return line feed)



Simple Strings start with a '+'
Followed by the string 'Pong'
Folllowed by a CRLF '\r\n'

+PONG\r\n

Minimal overhead because it requires n+3 bytes in response

==============================================================
Integers
intergers start with a ':'
Followed by the integer '1729'
Followed by the CRLF '\r\n'

:1729\r\n

==============================================================

Bulk String (Bulk string is binary safe)
we add prefix to that we get to know how many bytes to read

Bulk string start with a '$'
Followed by the number of bytes
Followed by a CRLF '\r\n'
Followed by the achual string
Followed by a CRLF '\r\n'


$4\r\nPONG\r\n

Why we need Bulk stirng
Simple string are not binary safe (can contain any byte)
Simple string cannot contain \r\n
can be used to store any binary data even a PNG image

Some special string

Empty stirng $0\r\n\r\n
Null value $-1\r\n

===============================================================

Arrays 

Arrays start with a ''

