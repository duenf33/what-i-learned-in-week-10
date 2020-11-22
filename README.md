# What-I-learned-in-week-10
## **Readline module :** <br>
The readline module provides an interface for reading data from a *`Readable stream`* one line at a time. It can be accessed using:
```javascript
const readline = require('readline');
```
---
*`Readable streams`*. A readable stream lets you read data from a source. The source can be anything. It can be a simple file on your file system, a buffer in memory or even another stream. As streams are EventEmitters , they emit several events at various points.

Examples of Readable streams include:
* HTTP responses, on the client
* HTTP requests, on the server
* fs read streams
* zlib streams
* crypto streams
* TCP sockets
* child process stdout and stderr
* `process.stdin` . - means "input coming from the terminal"
---
> Reading a line in NodeJS is very weird.<br> 
Here's one way to do it ↘︎
```javascript
process.stdin.once('data', 
(chunk) => { console.log(chunk.toString()) } )

```
>`once` is a function that takes *two parameters*, and its *second* *parameter* is another function
---
> and here is a nice way of looking at it ↘︎

| phrase | 	meaning |
| --- | ---|
|process.stdin| 	hey terminal input,|
|.once('data', ... )| 	when you get some data,|
|(chunk)| 	please name it chunk|
|=>| 	and send it to|
|{ ... }| 	this block of code|
|console.log(chunk.toString())| 	convert it to a string and print it to the terminal|

###### [click here to find out more about this.](https://codelikethis.com/lessons/javascript/input-and-output#using_readline__explanation)

---
The following simple example illustrates the basic use of the readline module ↘︎
```javascript
const readline = require('readline');

const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});

rl.question('What do you think of Node.js? ', (answer) => {
  // TODO: Log the answer in a database
  console.log(`Thank you for your valuable feedback: ${answer}`);

  rl.close();
});
```
Once this code is invoked, the Node.js application will not terminate until the readline.Interface is closed because the interface waits for data to be received on the input stream.
