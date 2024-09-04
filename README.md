# gRPC
Remote Procedure Call (RPC) is a protocol that allows a program to execute a procedure (subroutine) on a different address space, typically on another machine in a network. The goal of RPC is to make a remote procedure call appear as if it were a local call, abstracting the complexity of network communication from the developer.

## Key Concepts of RPC
### Client-Server Model:

- Client: The machine or process that initiates the RPC call.
- Server: The machine or process that executes the requested procedure and returns the result.
### Transparency:

- RPC provides transparency to the developer, meaning the programmer writes code as if they are making local procedure calls, without needing to worry about the complexities of network communication.
The network interaction (sending the request, waiting for the response, etc.) is hidden from the developer.

### Stub Functions:

- Client Stub: On the client side, a stub function acts as a proxy for the actual remote procedure. When the client calls this stub, it marshals (serializes) the procedure's parameters and sends them over the network to the server.
- Server Stub: On the server side, the stub receives the marshaled parameters, unmarshals (deserializes) them, and invokes the actual procedure on the server. After the procedure executes, the server stub marshals the result and sends it back to the client.
### Marshaling/Unmarshaling:

- Marshaling: The process of converting procedure arguments and results into a format that can be transmitted over the network (like a byte stream).
- Unmarshaling: The process of converting the received byte stream back into usable data structures.

### Transport Protocols:

- RPC can use various transport protocols, such as TCP/IP or UDP. TCP is more reliable but slower, while UDP is faster but less reliable.
Some RPC implementations might use HTTP/HTTPS as a transport protocol, especially in web-based services (e.g., JSON-RPC).
Synchronous and Asynchronous Calls:

- Synchronous RPC: The client waits (blocks) until the procedure on the server is executed and a response is returned.
Asynchronous RPC: The client does not wait for the server to complete the procedure and can continue executing other tasks. The response might be handled through callbacks or polling.

### Error Handling:

- Network failures, server unavailability, or other issues can cause RPCs to fail. Proper error handling mechanisms are essential to manage retries, timeouts, and partial failures.

### Types of RPC Protocols
- ONC RPC (Open Network Computing RPC):

  - Developed by Sun Microsystems, it's one of the original implementations of RPC.
  - It uses XDR (External Data Representation) for data serialization and typically runs over UDP or TCP.

- DCE/RPC (Distributed Computing Environment/RPC):

  - Developed by the Open Software Foundation (OSF), used in many enterprise environments.
  - Forms the basis for Microsoft's COM and DCOM (Distributed Component Object Model) technologies.

### gRPC:

- Developed by Google, it uses Protocol Buffers (protobuf) for data serialization.
gRPC supports multiple programming languages and is highly performant, making it popular in microservices architectures.
It runs over HTTP/2, which supports bidirectional streaming, flow control, and header compression.
JSON-RPC and XML-RPC:

- These are simpler, text-based RPC protocols that use JSON or XML for data serialization.
They are commonly used in web services, where lightweight and human-readable formats are advantageous.

### Advantages of RPC
- Abstraction: Developers can focus on the logic of their programs without worrying about the details of network communication.
- Language Independence: RPC allows programs written in different programming languages to communicate with each other.
- Ease of Use: The RPC model is straightforward for developers familiar with local procedure calls.

### Disadvantages of RPC
- Tight Coupling: RPC can lead to a tightly coupled system, where the client and server depend heavily on each other, making changes and scaling more difficult.
- Complexity in Error Handling: Network issues, server failures, or other errors can make error handling more complex in an RPC system.
- Performance Overhead: The overhead of marshaling/unmarshaling and network communication can impact performance, especially in high-latency networks.

### Use Cases of RPC
- Distributed Systems: RPC is often used in distributed computing environments where different components of an application run on different machines.
- Microservices: gRPC is widely used in microservices architectures for efficient, language-agnostic communication between services.
- Legacy Systems: Many older systems still rely on RPC, especially in enterprise environments.
RPC is a powerful concept that enables distributed computing by abstracting the complexity of network communication, making it easier to build systems where components communicate across different machines.
