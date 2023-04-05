# Real-time Chat Web App
This code is an implementation of a chat application built using the Rocket web framework in Rust programming language.

## Usage
```
cargo run
```
Open two windows simultaneously and starts chat! Note that once you refresh the window, all messages will lost.

## Explanation
### Struct
The code defines a `Message` struct that represents a message sent by a user in a chatroom. The struct has three fields:  
1. `room` representing the chatroom  
2. `username` representing the user's username  
3. `message` representing the message content  
The struct also has attributes for form validation, serialization, and deserialization.

The code uses the `rocket::State` struct to manage the broadcast queue, and the `rocket::Shutdown` struct to gracefully shutdown the server. The code also uses the `rocket::serde` crate for serialization and deserialization.
### Routes
The code defines two routes, `events` and `post`, that are mounted on the `/events` and `/message` endpoints, respectively.  
1. The events route returns an infinite stream of server-sent events. The events are messages pulled from a broadcast queue sent by the post route.   
2. The post route receives a message from a form submission and broadcasts it to any subscribers in the chatroom.  
### Server
The `#[launch]` macro defines the Rocket application and launches the server. The application is defined by creating an instance of `rocket::Rocket` using the `rocket::build()` function. The broadcast queue is managed using the `manage()` method, and the routes are mounted using the `mount()` method. The application serves static files using the `rocket::fs::FileServer` struct.

## References

* [rust-cli-template](https://github.com/kbknapp/rust-cli-template)
