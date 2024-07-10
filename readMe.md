What is Node.js and what is it used for?

Node.js is a runtime environment that allows you to run JavaScript code on the server side. It is used for building scalable network applications, particularly web servers and APIs, due to its non-blocking, event-driven architecture.
Explain the main differences between Node.js and traditional web server environments like Apache or Nginx.

Node.js:
Single-threaded and event-driven.
Handles multiple connections with a single thread using non-blocking I/O.
Often used for real-time applications.
Apache/Nginx:
Multi-threaded or multi-process.
Uses blocking I/O.
Better suited for serving static content and traditional web applications.
What is the V8 engine and how does Node.js utilize it?

V8 is the JavaScript engine developed by Google, used in the Chrome browser. It compiles JavaScript code into machine code. Node.js uses the V8 engine to execute JavaScript on the server side.
Describe the event-driven architecture of Node.js.

Node.js uses an event-driven architecture where an event loop handles asynchronous operations. When an event occurs (e.g., I/O operations), a callback function is executed, allowing Node.js to perform non-blocking I/O and handle many connections simultaneously.
What are some common use cases for Node.js?

Real-time applications (e.g., chat apps, gaming servers)
APIs and microservices
Single Page Applications (SPAs)
Data streaming applications
Server-side web applications
How does Node.js handle asynchronous operations?

Node.js uses callbacks, promises, and async/await to handle asynchronous operations. The event loop processes events and executes callback functions when operations are complete, allowing other tasks to proceed without waiting.
What is the purpose of the package.json file in a Node.js project?

The package.json file contains metadata about the project, including its dependencies, scripts, version, and other project information. It is essential for managing and sharing Node.js projects.
Explain the role of the Node Package Manager (NPM).

NPM is the default package manager for Node.js. It allows developers to install, share, and manage dependencies and packages in Node.js projects.
What is the node_modules folder and why is it important?

The node_modules folder stores all the installed packages and dependencies for a Node.js project. It is crucial for the project to function correctly, as it contains all the code needed for the dependencies.
How can you check the version of Node.js and NPM installed on your system?

You can check the version of Node.js by running node -v and the version of NPM by running npm -v in the terminal.
How does Node.js handle concurrency and what are the benefits of this approach?

Node.js handles concurrency using a single-threaded event loop and non-blocking I/O operations. This approach allows it to handle many connections simultaneously with minimal overhead, making it efficient for I/O-bound tasks.
How does Node.js handle file I/O? Provide an example of reading a file asynchronously.

Node.js uses the fs module for file I/O operations. Example of reading a file asynchronously:
javascript
Copy code
const fs = require('fs');

fs.readFile('example.txt', 'utf8', (err, data) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(data);
});
What are streams in Node.js and how are they useful?

Streams are objects that allow you to read or write data piece by piece. They are useful for handling large amounts of data efficiently, such as reading files, network communications, or any data transfer operations.
Node.js Modules
What are modules in Node.js and why are they important?

Modules are reusable pieces of code that can be included in other files. They help organize code, make it more manageable, and promote reuse.
How do you create a module in Node.js? Provide a simple example.

Example of creating a module:
javascript
Copy code
// math.js
function add(a, b) {
  return a + b;
}

module.exports = add;

// main.js
const add = require('./math');
console.log(add(2, 3)); // Output: 5
Explain the difference between require and import statements in Node.js.

require is used in CommonJS module system and is synchronous. import is used in ES6 modules and is asynchronous. Node.js supports both, but import requires enabling ES modules.
What is the module.exports object and how is it used?

module.exports is an object that is returned as the result of a require call. It is used to define what a module exports and makes available to other files.
Describe how you can use the exports shorthand to export module contents.

You can use exports as a shorthand to attach properties or methods to module.exports.
javascript
Copy code
// math.js
exports.add = (a, b) => a + b;
exports.subtract = (a, b) => a - b;
What is the CommonJS module system?

CommonJS is a module system used in Node.js where each file is treated as a separate module. It uses require to load modules and module.exports to export them.
How can you import a module installed via NPM in your Node.js application?

You can import a module installed via NPM by using require.
javascript
Copy code
const express = require('express');
Explain how the path module works in Node.js. Provide an example of using it.

The path module provides utilities for working with file and directory paths.
javascript
Copy code
const path = require('path');

const filePath = path.join(__dirname, 'example.txt');
console.log(filePath);
How do you handle circular dependencies in Node.js modules?

Circular dependencies can be managed by breaking the dependency chain or restructuring the code to avoid mutual dependencies. Node.js handles them by returning an incomplete version of the module.
What is a built-in module in Node.js? Name a few and explain their purposes.

Built-in modules are modules provided by Node.js out of the box, such as:
http: Used to create HTTP servers.
fs: File system operations.
path: Utilities for working with file paths.
os: Provides operating system-related utility methods.
What is the difference between relative and absolute module paths in Node.js?

Relative paths start with ./ or ../ and are relative to the current file. Absolute paths start from the root directory or use the full path.
What is a module wrapper function in Node.js?

Node.js wraps each module in a function before executing it. This function provides a private scope for the module, giving access to exports, require, module, __filename, and __dirname.
Describe the buffer module and its use in Node.js.

The Buffer module handles binary data directly. It is used for reading or manipulating streams of binary data, such as file or network I/O.
Starting an HTTP Server in Node.js
How do you create a simple HTTP server in Node.js? Provide a code example.

javascript
Copy code
const http = require('http');

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello, World!\n');
});

server.listen(3000, '127.0.0.1', () => {
  console.log('Server running at http://127.0.0.1:3000/');
});
Explain the purpose of the http module in Node.js.

The http module provides utilities to create HTTP servers and clients, allowing Node.js to handle HTTP requests and responses.
What method do you use to start the HTTP server and make it listen on a specific port?

Use the listen method to start the server and specify the port and hostname.
javascript
Copy code
server.listen(port, hostname, callback);
How can you send a response to the client in an HTTP server created with Node.js?

You can use the res.write() and res.end() methods to send a response.
javascript
Copy code
res.write('Hello, World!');
res.end();
Explain the request and response objects in the context of an HTTP server.

The request object contains information about the client's request (e.g., URL, headers, method).
The response object is used to send back a response to the client (e.g., status code, headers, body).
How do you handle different HTTP methods (GET, POST, etc.) in a Node.js HTTP server?

Check the req.method property and handle accordingly.
javascript
Copy code
if (req.method === 'GET') {
  // Handle GET request
} else if (req.method === 'POST') {
  // Handle POST request
}
What is middleware in the context of a Node.js HTTP server?

Middleware functions are functions that have access to the request and response objects, and can modify them or end the request-response cycle. They are used for tasks such as authentication, logging, and request parsing.
How can you serve static files using an HTTP server in Node.js?

Use the fs module to read and serve static files.
javascript
Copy code
const fs = require('fs');
const path = require('path');

const server = http.createServer((req, res) => {
  const filePath = path.join(__dirname, 'public', req.url);
  fs.readFile(filePath, (err, data) => {
    if (err) {
      res.statusCode = 404;
      res.end('File not found');
    } else {
      res.statusCode = 200;
      res.end(data);
    }
  });
});
Explain how to handle errors in an HTTP server created with Node.js.

Use try-catch blocks or error-handling middleware to handle errors.
javascript
Copy code
server.on('error', (err) => {
  console.error('Server error:', err);
});
How can you implement routing in a Node.js HTTP server without using external libraries?

Use if-else statements or a routing table to handle different routes.
javascript
Copy code
const server = http.createServer((req, res) => {
  if (req.url === '/' && req.method === 'GET') {
    res.statusCode = 200;
    res.end('Home Page');
  } else if (req.url === '/about' && req.method === 'GET') {
    res.statusCode = 200;
    res.end('About Page');
  } else {
    res.statusCode = 404;
    res.end('Page not found');
  }
});