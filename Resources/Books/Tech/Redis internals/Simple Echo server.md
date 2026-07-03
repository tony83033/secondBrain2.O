#echoServer
```node
const net = require('net');

const PORT = "7379";
const HOST = "0.0.0.0";

const server = net.createServer((socket)=>{
    console.log("Client connected",socket.remoteAddress, socket.remotePort);

    socket.on("data",(data)=>{
        const input = data.toString();
        console.log("Received:\n", input);

        // Special case: prevent redis-cli crash
        if (input.includes("COMMAND")) {
            socket.write("*0\r\n"); // empty array
            return;
        }

        // Echo back as RESP bulk string
        const response = `$${input.length}\r\n${input}\r\n`;
        socket.write(response);

    });

    socket.on("end",()=>{
        console.log("Client disconnected");
    });

    socket.on("error",(err)=>{
        console.log("Socket err: ",err.message);
    });
})

server.listen(PORT,HOST,()=>{
    console.log("Server is listening on  ",{HOST},{PORT});
});
```

