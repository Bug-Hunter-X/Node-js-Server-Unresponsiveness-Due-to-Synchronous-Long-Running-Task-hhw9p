# Node.js Server Unresponsiveness

This repository demonstrates a common issue in Node.js where a long-running synchronous operation in the request handler blocks the event loop, causing the server to become unresponsive.

## Problem
The `server.js` file contains a simple HTTP server that simulates a long-running task within the request handler. This task keeps the CPU busy for 5 seconds, preventing the server from handling any other requests during that time.

## Solution
The `serverSolution.js` file demonstrates how to solve the problem by using asynchronous operations. This allows other requests to be processed while the long-running task is executing.

## How to reproduce
1. Clone this repository.
2. Run `node server.js`.
3. Try to make multiple requests to the server (e.g., using `curl` or a browser).
4. Observe that the server becomes unresponsive for 5 seconds after each request.
5. Now run `node serverSolution.js` and repeat steps 3 and 4. Observe the server remains responsive.

## Lessons Learned
- Avoid long-running synchronous operations in Node.js request handlers.
- Use asynchronous operations (e.g., `setTimeout`, `setInterval`, promises, async/await) to prevent blocking the event loop.