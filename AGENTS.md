# Global rules

- Read and strictly follow the project's AGENTS.md before taking any action. Do not gloss over it.

## Context Management & Token Optimization

- **Proactively compress context** after:
  - A skill completes its task and the work is done
  - Long back-and-forth conversations that are resolved
  - Transitioning to a new major topic
  - Loading large skills (architect, composio-cli, etc.) that consume significant tokens

- **Be mindful of token consumption**:
  - Skills add their full content to context when called
  - Compress skill content out once it's no longer needed
  - Keep context lean for better performance and lower costs

- **Ask the user before compressing** if you're unsure whether previous context is still needed
