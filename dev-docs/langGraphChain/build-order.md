# Build order

#### Parent Graph 1

1. `config`
    * Define `SYSTEM_PROMPT` type `SystemMessage`

2. `schema`
    * Pydantic models (external contract)

3. `state`
    * For graph and subgraphs
    * TypedDict + Reducers

#### Subgraphs

1. `state`
    * For graph and subgraphs
    * TypedDict + Reducers

2. `tools`
    * Expost a list of tools

3. `nodes`
    * Contains node funcitons- that accept `state`, `config`, `runtime`

4. `graph.py`
    * Build agent subgraph using `StateGraph`
    * Bind tools once at graph build runtime

#### Parent Graph 2

1. `graph.py`
    * Initialize `checkpointer`
    * Compose subgraphs (as nodes)
    * Add router logic (pick which agents to run)
    * Add final formatting node
    * Implement **stream events** using `.astream()`, `stream_mode=["updates","messages","custom"]` and `get_stream_writer()` for custom progress inside tools/nodes.