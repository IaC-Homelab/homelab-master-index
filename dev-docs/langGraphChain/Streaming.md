# Streaming

Display output progressivley

* Stream agent progress - updates after each agent step.
* Stream LLM tokens as they're generated.
* Stream custom updates (ex: Fetched 10/100 records)

### Streaming modes

Pass  one or more stream mode as list to `astream` method

* `updates` - Streams state update after each agent step.
* `messages` - Streams tuples of `(token, metadata)` from any graph node LLM is invoked.
* `custom` - Streams custom data from inside graph nodes using stream writer.

### Agent progress (updates)
Use `astream` method with `stream_mode="updates"`. This emits an event after every agent step.

### LLM tokens (messages)
Stream tokens produced by LLM use `stream_mode="messages"`. 

### Custom 
Stream custom updates from tools as they are executed use `get_stream_writer` in the tool funciton.