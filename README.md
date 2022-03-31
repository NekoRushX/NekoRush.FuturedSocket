## Futured Socket

This is a pure async/await socket wrapper  
based on the legacy socket.

## Example

```C#
// Create a new futured socket instance
 var client = new FuturedSocket(AddressFamily.InterNetwork, 
                                SocketType.Stream, ProtocolType.Tcp);
{
    // Connect to the server
    var connected = await client.Connect("127.0.0.1", 23333);
    if(!connected) return false;
    
    // Send a message
    var sent = await client.Send("Hello World!");
    if(sent <= 0) return false;
    
    // Receive a message
    var buffer = new byte[255];
    var received = await client.Receive(buffer);
    if(received <= 0) return false;
    
    // Print the received message
    Console.WriteLine(Encoding.UTF8.GetString(buffer[..received]));
}

// Disconnect from the server
await client.Disconnect();
client.Dispose();
```
