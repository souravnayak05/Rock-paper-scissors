# AI Game Referee – Rock Paper Scissors Plus

## State Model

The game state is maintained using a structured in-memory Python dictionary that persists across conversational turns. It tracks the current round number, user and bot scores, and whether the special bomb move has already been used by each player. This ensures strict enforcement of the three-round limit and one-time bomb usage rule. State is never stored only in the prompt and is updated exclusively through defined tools.

## Agent and Tool Design

The system is designed with a clear separation between intent understanding, game logic, and response generation. User input is first interpreted as an attempted move. Core game logic is encapsulated in explicit tool functions. The validate_move tool verifies move validity and enforces bomb usage constraints, while handling invalid inputs gracefully. The resolve_round tool applies deterministic game rules to decide the round outcome and update scores. This modular approach aligns with Google ADK principles by isolating state mutation from conversational output.

## Tradeoffs

To keep the implementation minimal and focused on correctness, the bot’s move selection is randomized rather than strategy-based. The interaction is implemented as a simple conversational loop instead of a full chat UI or multi-agent setup. Structured outputs are kept lightweight to reduce complexity while maintaining clarity.

## Future Improvements

With additional time, the system could be enhanced with a strategy-driven bot, richer intent classification, and fully structured JSON outputs for easier UI integration. Further improvements could include a formal Google ADK agent schema and more expressive conversational feedback.
