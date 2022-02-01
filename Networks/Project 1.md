# [Project 1]([Project 1: Socket Basics - CS 3700](https://3700.network/docs/projects/socketbasics/))
- Erroneous response from the server (but assume not malicious responses, just incorrectly formatted or missing a field) -> Catch and print a helpful error message and then exit (gracefully, instead of with a stack trace)
- Listens for non-encrypted requests on TCP socket bound to port 27993
- [Word list](https://3700.network/projects/project1-words.txt)
- Must execute on command line with `$ ./client <-p port> <-s> <hostname> <Northeastern-username>` *exactly*
	- `-p port`  is optional; specifies TCP port the server is listening on. If not supplied, assume port is 27993.
	- `-s` optional; if given, client should use TLS encrypted socket connection. If this is supplied and `-p` not specified, assume that the port is 27994.
	-  `hostname` required, specifies name of server (either DNS name or IP address in dotted notation).
	-   The `Northeastern-username` parameter is required.
## Messages
String JSON w/ fields delimited by spaces, terminated by \n
`<JSON formatted data>\n`

Types:
- hello `{"type": "hello", "northeastern_username": "liu.mel"}\n`
- start `{"type": "start", "id": <string>}\n`  the `<string>` is a random string selected by the server that represents this game ID; your client needs to remember this ID for future messages
- guess `{"type": "guess", "id": <string>, "word": <string>}\n`
- `retry`
- bye `{"type": "bye", "id": <string>, "flag": <string>}\n`
- error `{"type": "error", "message": <string>}\n`

## Receive
0 - Letter doesn't appear
1 - Letter appears in different position
2 - Correct letter and position

If > 500 guesses, sends error and closes connection

If word correct: 
- Secret flag retrieved from a non TLS encrypted socket
- Secret flag retrieved from a TLS encrypted socket

### Example
Start game to get ID for instance, Guess, 
`C -> S: {"type": "hello", "northeastern_username": "amislove}\n 
S -> C: {"type": "start", "id": "foo"}\n 

C -> S: {"type": "guess", "id": "foo", "word": "treat"}\n 
S -> C: {"type": "retry", "id": "foo", "guesses": [{ "word": "treat", "marks": [1, 0, 2, 2, 0]}]}\n 

C -> S: {"type": "guess", "id": "foo", "word": "sweat"}\n 
S -> C: {"type": "retry", "id": "foo", "guesses": [{ "word": "treat", "marks": [1, 0, 2, 2, 0]}, { "word": "sweat", "marks": [2, 0, 2, 2, 1]}]}\n 
C -> S: {"type": "guess", "id": "foo", "word": "steam"}\n 
S -> C: {"type": "bye", "id": "foo", "flag": "sndk83nb5ks&*dk*SKDFHGk"}\n`