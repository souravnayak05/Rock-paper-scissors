AI Game Referee – Rock Paper Scissors Plus
State Model

The game state is maintained using a structured in-memory Python dictionary that persists across conversational turns. The state tracks the current round number, user and bot scores, and whether the special bomb move has already been used by either player. This approach ensures strict enforcement of game constraints such as the three-round limit and one-time bomb usage, while avoiding reliance on prompt-only memory. State updates occur only through defined tools, ensuring predictable and debuggable behavior.

Agent and Tool Design

The system is designed with a clear separation between intent understanding, game logic, and response generation. User input is first interpreted as an attempted move. Core game logic is encapsulated within explicit tool functions. The validate_move tool verifies move legality and enforces bomb usage rules, while gracefully handling invalid inputs. The resolve_round tool applies deterministic game rules to determine the round outcome and update scores. This modular design mirrors Google ADK principles by isolating state mutation and rule enforcement from conversational output generation.

Tradeoffs

To keep the implementation minimal and focused on correctness, the bot’s move selection is randomized rather than strategy-driven. The interaction is implemented as a simple conversational loop instead of a full chat interface or multi-agent setup. Structured output schemas were kept lightweight to reduce complexity while still maintaining clarity and correctness.

Future Improvements

With additional time, the system could be enhanced by introducing a strategic bot policy, richer intent classification, and fully structured JSON outputs for easier UI integration. A more formal Google ADK agent schema and improved conversational explanations could further enhance clarity and extensibility.
