# Enterprise Integration

**Enterprise Integration** is the task of making separate applications work together to produce a unified set of functionality. 

**Synchrononous** is a process by which a procedure waits for its subprocedure to execute. In other words, a synchronous operation **blocks** a process till the operation completes.

**Asynchronous** is a process by which a procedure does not want to wait for its subprocedure to execute but want to invoke asynchronously by starting the subprocess, execute in the background and notify when completed. In other words, an asynchronous operation is **non-blocking** and only initiates the operation and process completion is notified later.

**Asynchronous messaging architectures** have proven to be the best strategy for enterprise integration because they allow for a loosely coupled solution that overcomes the limitations of remote communication, such as latency and unreliability.

**Application Integration Options**
 * File Transfer - One application writes a file that another later reads, the applications need to agree on the filename, location and the format of the file.
 * Shared Database - Multiple applications share the same database schema, located in a single physical database. Because there is no duplicate data storage, no data has to be transferred from one application to the other
 * Remote Procedure Call - One application exposes some of its functionality so that it can be accessed remotely by other applications as a remote procedure. The communication occurs real-time and synchronously.
 * Messaging -  One applications publishes a message to a common message channel. Other applications can read the message from the channel at a later time. The applications must agree on a channel as well as the format of the message. The communication is asynchronous.
 
## What is Messaging?
* Messaging is a technology that enables high-speed, asynchronous, program-to-program communication with reliable delivery. 
* Programs communicate by sending packets of data called **messages** to each other.
* **Channels**, also known as queues, are logical pathways that connect the programs and convey messages.
* A **receiver** or **consumer** is a program that receives a message by reading (and deleting) it from a channel.
* A **message** actually contains two parts, a **header** and a **body**. The header contains meta-information about the message—who sent it, where it’s going, etc.; The body contains the data being transmitted and is ignored by the messaging system.

## Benefits of Messaging 
* __Remote Communication__ - Messaging enables separate applications to communicate and transfer data. 
* __Asynchronous Communication__ - Messaging enables a send and forget approach to communication. The sender does not have to wait for the receiver to receive and process the message; it does not even have to wait for the messaging system to deliver the message.
* __Asynchronous Communication__ - Messaging enables a send and forget approach to communication. The sender does not have to wait for the receiver to receive and process the message; it does not even have to wait for the messaging system to deliver the message.
* __Throttling__ - A problem with remote procedure calls is that too many of them on a single receiver at the same time can overload the receiver.
* __Reliable Communication__ - Messaging provides reliable delivery that a remote procedure call (RPC) cannot.
* __Mediation__ - The messaging system acts as a mediator between all of the programs that can send and receive messages.
* __Thread Management__ - Asynchronous communication means that one application does not have to block while waiting for another application to perform a task, unless it wants to.
