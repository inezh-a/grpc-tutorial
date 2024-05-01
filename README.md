### Reflection
1. What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable?
> - Unary: Client sends a single request to the server, and a single response gets sent back. Suitable for fetching data and other simple query-response types of interaction.
> - Server streaming: Client sends a single request to the server, server then sends a stream of responses back. Suitable for downloading large amounts of data in manageable continuous chunks or for receiving updates over time.
> - Bi-directional streaming: Both client and server can send streams of messages concurrently. Suitable for real-time communication, online gaming, and others where there is a need for bi-directional data flow.
2. What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption?
> - Authentication: to verify that the client is who they say they are. Can be done through authentication mechanisms such as OAuth, JWT Tokens, or mutualTLS (mTLS).
> - Authorization: to ensure that the client have the appropriate permissions to perform certain actions. Can be implemented using role-based access control (RBAC) or attribute-based access control (ABAC) policies. 
> - Data Encryption: to protect data in transit, safeguarding sensitive information from unauthorized access. Can be done using TLS Encryption which gRPC supports by default.
3. What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications?
> - Error Handling: Dealing with errors that occur during bi-directional streaming gracefully, such as network interruptions or client disconnects.
> - Concurrency: Managing concurrent message processing and the resources that is needed for it efficiently, which is important in scenarios like comm-applications with potentially tons of active connections.
4. What are the advantages and disadvantages of using the tokio_stream::wrappers::ReceiverStream for streaming responses in Rust gRPC services?
> - Advantages: Provides a convenient way to convert a receiver into a stream, making it compatible with gRPC streaming. Simplifies the integration of asynchronous streaming into Rust gRPC services.
> - Disadvantages: Less control over streaming behavior compared to custom implementations and adds complexity as it may require additional error-handling code, among other things.
5. In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time?
> - Package functionality into reusable modules and structs.
> - Use traits to define common behaviors and aids in code reuse.
> - Separate concerns by following SOLID principles (Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion).
> - Using dependency injection to decouple components and facilitate testing and future modifications.
6. In the MyPaymentService implementation, what additional steps might be necessary to handle more complex payment processing logic?
> Additional security mechanisms should be employed in a more complex payment processing logic. Mechanisms such as authentication, authorization, encryption is especially important when handling payments. Extra protective measures may also be deployed to protect from user-error, like fraud-detection.
7. What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms?
>  gRPC promotes interoperability across languages and platforms due to Protocol Buffers, which provides a language-agnostic way to define the structure of messages and services. Essentially, it allows developers to automatically generate client and server code in multiple programming languages.
8. What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs?
> - Advantages: HTTP/2 offers multiplexed streams, header compression, and server push, resulting in reduced latency and improved efficiency, which are beneficial for real-time communication in gRPC.
> - Disadvantages: More complexity in it's implementation, which may lead to difficulty in maintaining and troubleshooting compared to HTTP/1.1. It may also face compatibility issues with older clients not supporting HTTP/2.
9. How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness?
> REST APIs follows a request-response model, suitable for synchronous interactions where clients initiate requests and wait for responses. This model is suitable for scenarios where real-time communication and responsiveness are not important, as it may involve delays. gRPC's bidirectional streaming capabilities enable real-time communication with it's lower latency and overhead, making it more suitable for scenarios requiring continuous data exchange, such as chat applications or live updates.
10. What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads?
> gRPC's Protocol Buffers provide strong typing and schema enforcement, facilitating interoperability between different systems and programming languages. Protocol Buffers are also designed for efficient serialization and deserialization of data, resulting in smaller payload sizes and faster processing compared to JSON. JSON, meanwhile, allows for more flexibility as it does not enforce a strict schema, allowing developers to send and receive data with varying structures. This allows easier data-modelling, but may lead to issues and inconsistencies over time.
