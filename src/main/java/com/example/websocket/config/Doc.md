The @EnableWebSocketMessageBroker is used to enable our WebSocket server. We implement WebSocketMessageBrokerConfigurer interface and provide implementation for some of its methods to configure the websocket connection.

In the first method, we register a websocket endpoint that the clients will use to connect to our websocket server.

Notice the use of withSockJS() with the endpoint configuration. SockJS is used to enable fallback options for browsers that don’t support websocket.

You might have noticed the word STOMP in the method name. These methods come from Spring frameworks STOMP implementation. STOMP stands for Simple Text Oriented Messaging Protocol. It is a messaging protocol that defines the format and rules for data exchange.

Why do we need STOMP? Well, WebSocket is just a communication protocol. It doesn’t define things like - How to send a message only to users who are subscribed to a particular topic, or how to send a message to a particular user. We need STOMP for these functionalities.

In the second method, we’re configuring a message broker that will be used to route messages from one client to another.

The first line defines that the messages whose destination starts with “/app” should be routed to message-handling methods (we’ll define these methods shortly).

And, the second line defines that the messages whose destination starts with “/topic” should be routed to the message broker. Message broker broadcasts messages to all the connected clients who are subscribed to a particular topic.

In the above example, We have enabled a simple in-memory message broker. But you’re free to use any other full-featured message broker like RabbitMQ or ActiveMQ.
