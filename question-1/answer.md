Node.js architecture is single-threaded but non-blocking, using an event loop powered by libuv to handle async operations efficiently.[Attachment +2]
1. Node.js Architecture Details
It starts with incoming requests (simple or complex) hitting the Node.js server, which queues them in an event queue. The single main thread runs the event loop to process callbacks sequentially, while libuv offloads blocking tasks like file I/O or crypto to a thread pool (default 4 threads).[geeksforgeeks +2]
2. What is Thread Pool?
Thread pool is a group of background worker threads (usually 4) in libuv that handle CPU-intensive or blocking ops without stalling the main event loop.[shiftasia]
3. Questions Handled by Thread Pool
Heavy tasks that’d block JS, like file reads/writes (fs module), DNS lookups, crypto hashing (pbkdf2), or compression.[dev +1]
4. What are Worker Threads?
Worker Threads (from ‘worker_threads’ module) let you spawn true parallel threads for CPU-bound work, unlike thread pool’s limited I/O focus—great for heavy computations.[w3schools]
5. Event Loop Between Thread Pool & Worker Threads
Event loop stays on main thread: offloads to thread pool for I/O (they callback when done), queues results for loop; worker threads run separate JS contexts, message back via postMessage to main loop.