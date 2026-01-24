# Build order

### Think about

- [ ] Return only `reply` + `thread_id`. - returning full histroy gets expensive-
- [ ] Add `GET /sessions/{thread_id} for history

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
    * Functions of actual work
    * Expost a list of tools
    * tools = function

3. `nodes`
    * Reads state, does some work (LLM call, tool call, validation, DB write, etc)
    * Contains node funcitons- that accept `state`, `config`, `runtime`
    * Defines an `AGENT_SYSTEM_PROMPT`
    * nodes = step

4. `graph.py`
    * Build agent subgraph using `StateGraph`
    * Bind tools once at graph build runtime
    * graph = wiring between steps

#### Parent Graph 2

1. `graph.py`
    * Initialize `checkpointer`
    * Compose subgraphs (as nodes)
    * Add router logic (pick which agents to run)
    * Add final formatting node
    * Implement **stream events** using `.astream()`, `stream_mode=["updates","messages"]` then adding `["custom"]`. For custom progress inside tools/nodes use `get_stream_writer()`.