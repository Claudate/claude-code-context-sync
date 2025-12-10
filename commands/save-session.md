# Save Current Session

Use the `context-save` skill to save the current work context for resuming in another window.

This command will:
1. Analyze the current conversation context
2. Extract completed and pending tasks
3. Identify key files being worked on
4. Save everything to `docs/context-sessions/` directory

The saved session can be resumed later using `/resume-session` command.
