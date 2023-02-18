# node_refresh

## Node process ->c++ program
use so called single thread (sequence of instructions)

Initialize program (register) -> execute 'top-level' code (no callback) ->require modules -> registger event callbacks -> start event loop (but some task is to heavy, which will block other process)

libuv async io layer link to underlying computer operating system, file system, networking

Thread pool(provide multiple thread 4-128) event loop offloading heavy task to the thread pool
eg: file system API, Cryptography, compression, DNS lookups

## Event loop
run callback functions (function that called asa other work finished)

### event driven architecture
events are emitted
event loops picks them up
callbacks are called

event loop do orchestration (receive events, call callback functions, offload expensive task to thread pool)

different phase have different queue, 
1. take timer callbacks (eg: settimeout)
if timer finished, callback function will only be called when Node back to timer phase

2. I/O polling (input output, networking, file access)

3. setimmediate callback 

4. close callback (websocket shut down)


