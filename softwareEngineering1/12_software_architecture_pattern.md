# Software Architecture Pattern

* Is a system level pattern and provides a system level layout or application framework. 

## Layered Architecture Pattern
* `Presentation Layer`: Responsible for user interactions.
* `Application/Business Layer`: Handles functional requirements.
* `Domain Layer`: Business logic, algorithms and programming components
* `Persistent Database Layer`: Handling data

## Client Server Application Pattern
* 2 main parts, a client and a server.
* Centralized server computer that communicates with many clients over the internet.

## Peer to Peer Networks
* All systems act as both clients and servers to communicate.

## Publish Subscribe / Messaging Architecture Pattern
* When publishers need to deliver specific types of messages to specific subscribers.
* Publishers send messages to a third party with metadata regarding the type of message.
* Subscribers can then subscribe to specific types of messages which the third party then relays onto them.
* Allows for subscribers and publishers to have no knowledge of each other.
* Allows for subscribers to not have a need to be constantly online to receive messages.
* Allows for simplicity in the ends of the publishers and subscribers.

## Model View Controller Architecture Pattern
* Provides a clear separation of business logic into 3 components:
    * `Model`: The backend that contains the core functionality, business data and the application state.
    * `View`: User interface that shows data and supports interactions with the user.
    * `Controller`: The brains of the application that controls how data is displayed.