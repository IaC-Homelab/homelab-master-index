# Overview

## Agents

### Static models
Configured once when creating agent and remain unchanged.

### Dynamic models
Model is select at runtime based on current state and context. Created using `middleware`.

### Tools
Give agents the ability to take action. 
* Sequence or parallel tool calls
* Pass a list of tools to the agent

#### Tool error handling
* Done with `@Wrap_tool_call`
* Returns a message to the model. Agent returns a `ToolMessage` with custom error message when tool fails.

#### Tool use in ReAct loop
(Reasoning + Acting pattern) 

Reason: what tool to use → Act: call tool → Reason: next tool to use → Act: call tool → Reason: it has suffient info for final answer → Act: Produce final answer

### System prompt
Should be in type `SystemMessage`

#### Dynamic system prompt
* Use `middleware` decorater `@dynamic_prompt` to generate dynamic prompts based on model requests

### Structured output
`ToolStrategy` or `ProviderStrategy` 

### Memory

* "Short-term memory" Information stored in the state
* "Long-term memory" 

### Middleware
Customizing agent behavior at differen stages, can be used to:
* Process state before model is called (ex: trimming, context injection)
* Modify/validate model's response (ex: guardrails, filtering)
* Handle tool errors with custom logic
* Implement dynamic model selection based on state or context
* Add custom logging, monitoring or analytics

