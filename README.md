## Commit 1 Reflection notes

content of handle_connection:
- Take a tcp connection aka stream as an argument
- Make buffered reader wrapping the address of the stream
- Read each line of the stream until it reaches an empty line
- Gathers all lines into a Vector of strings
- The vector, which now contains an http requests, is printed



## Commit 2 Reflection notes

![Commit 2 screen capture](commit2.png)

new content of handle_connection:
- Same reading http request logic as commit 1 but no printing
- Make a http status line
- Read the contents of hello.html file
- Get the length of the file contents
- Build and format an http response with a status line, html page, and content length
- Write the http response to the stream so the client receives it

## Commit 3 Reflection notes

new content of handle_connection:
- Membaca baris pertama request
- Berdasarkan path request, kita conditionally set status_line & filename yang ditulis
- Respond dengan status_line & filename yang telah disesuaikan

## Commit 4 Reflection notes

By adding sleep we can see how loading other pages is stalled by the /sleep page load

## Commit 5 Reflection notes

Created a threadpool containing a max of 4 threads. Pool has a method to execute a job (code), the job being handle_connection function.

Execute method places the job in a queue (mpsc) for idle workers to take and run. Once finished running, worker is idle again and takes the next job waiting in queue.

This setup allows handling of multiple requests using multi threading, solving the problem caused by /sleep.

## Commit Bonus Reflection notes

Build method returns a result enum object which returns threadpool if successful or errors if unsuccessful