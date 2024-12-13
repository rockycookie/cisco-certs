### From the following options, what are the required REST API attributes?
- [x] Clear determination of whether a resource can be cached
- [ ] Dynamic interface
- [x] Uniform interface
- [ ] Peer-to-peer architecture

There are six required attributes for REST APIs:
- Client/server architecture (instead of P2P): REST APIs operate in the client/server model. This means that an application is built with RESTful APIs that act as the server. A client computer or device would make a RESTful API call to the application.
- Stateless operation: All of the state for the connections between client and server is actually on the client. The servers do not hold any state for that connection. This is good because it puts less load on the servers so they can process more requests. From a client perspective, the client must be sure to send the necessary information that the server will need to complete the request.
- Clear determination of whether a resource can be cached: With REST APIs, servers can cache the most used resources. This is usually used with GET requests. Caching can speed up the operations and the responses to the users.
- Uniform interface: In the RESTful world, everything is perceived to be a resource, no matter whether it’s a document, function, method, class, or module. This simple uniformity of interface leads to consistency and rapid deployment of new systems.
- Layered system: With REST APIs, you can leverage the single URI to complete any task at hand. In the background you have no idea that the URI you used actually ended up utilizing several servers/services in the back end.
- Code on demand: With REST APIs, you can determine what form of data you want back, and not just the values of data. If you want the form of data to be JSON, XML, or YAML, you can specify that. This is still all with a single URI because it’s just a value in the header of the request.
