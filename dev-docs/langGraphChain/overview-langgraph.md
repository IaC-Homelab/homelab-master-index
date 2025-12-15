# Overview

## Graph API

### State
Consists of `schema` and `reducer functions`.  
* `schema` made using `TypedDict` and `dataclass` to set default values
* `reducer functions` specifies how to apply updates to state
* Able to have a seperate internal private schema between nodes

### Reducers
Each key in `state` has its own reducer function. If no reducer function explicitly set, all updates to that key will override it.
* Use `Annotated` when defining the `schema` to add a reducer function
>__Overwrite__ bypass reducer and diretly overwrite a state value. Node would return a value wrapped with `Overwrite`. Good to reset or replace accumulated state instead of merging.

### Entry Point
first node(s) that run when graph starts.

### Conditional Entry Point
Start at different nodes depending on `routing_function` that will output name of next node.

### Nodes
* Input: `state`, `config`, `runtime`
    * config - object, contains config information like thread_id and tags.
    * runtime - object, that contains `runtime context` and other info like store and stream_writer
        * runtime context - used to pass information to nodes (via context param) that are not part of the graph state like names and db connections.
* Does: Reads the current shared state, Does some work (LLM call, tool call, validation, DB write, etc).
* Returns: updates for state- that get merged back into state

Nodes do "one unit" of work. Can have multiple outgoing edges.

### Edges
Answers: "Where to go after this node?". Two types, fixed (A → B) or conditional.
* Conditional - Attach `routing_function` (accepts current state, does logic and returns next node name)

> __Command__ Replaces conditional edge when you need a `state` update and `routing_function` in a single function.











## Persistence

Done with checkpointers via `checkpoint` of graph state at every super-step. Each checkpoint saved to a `thread` which can be accessed after graph execution.

### Threads
