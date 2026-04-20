## Commit 1 Reflection notes

content of handle_connection:
- Take a tcp connection aka stream as an argument
- Make buffered reader wrapping the address of the stream
- Read each line of the stream until it reaches an empty line
- Gathers all lines into a Vector of strings
- The vector, which now contains an http requests, is printed