# Javascript Basics

## Execution model (browser)

[What the heck is the event loop anyway?](https://www.youtube.com/watch?v=8aGhZQkoFbQ&t=710s)

* Event loop: JS is single-threaded: This thread executes the event loop and checks the task queue
* WebAPIs: Asynchronous calls use WebAPIs (Ajax, etc) to perform something as a background task
* Task queue: Finished background tasks add callback to the task queue
