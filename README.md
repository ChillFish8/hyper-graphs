# hyper-graphs
Some example diagrams to help understand the tokio/hyper ecosystem.

# The most common case - Server
The most common case you'll see is Hyper running on the tokio runtime. Tower provides a set of utilities and a basic middleware-based framework on top of hyper's lower level design to make it easier to build frameworks around hyper and / or use tower as a framework itself.

That said alot of frameworks also just use hyper directly e.g. [poem](https://github.com/poem-web/poem) or [thruster](https://github.com/thruster-rs/Thruster)

![Basic-Use drawio](https://user-images.githubusercontent.com/57491488/148132102-ecf5c8f5-d807-46b4-b95c-19fda75ca5cf.png)

# The most common case - Client
Hyper provides a client implementation which is reletively low level, this is because alot of the HTTP spec is shared by both client and server.

Reqwest is the only client I know built on hyper's client and it also provides it's own extensions like blocking / syncronous support. WASM I believe is completely seperate to hyper.

![Client](https://user-images.githubusercontent.com/57491488/148133506-4448a102-adb8-4694-8534-5f71f459b065.png)

# Hyper on other runtimes
Because hyper and it's relevant crates are generally generic over key parts e.g. IO layer and runtime. You can infact swap out things like tokio with say `async-std` or in some cases like [Google fuchsia](https://fuchsia.dev/) where they implemented their own IO / runtime handler and ran hyper on top of that.

# Hyper's internals on a diagram
![Internals](https://user-images.githubusercontent.com/57491488/148133066-67ee469c-e12f-4392-aabe-92e3c604c3e2.png)
