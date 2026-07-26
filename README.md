# aicommit

AI-powered git commit message generator using [opencode](https://opencode.ai/).

Automatically generates conventional commit messages based on your staged changes.

## Requirements

- [opencode](https://opencode.ai/) - installed and configured
- Bash
- Git

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/jakshi/aicommit.git
   ```

2. Install with just:
   ```bash
   just install
   ```

3. (Optional) Create a commit message template at `~/COMMITS.md` to customize the format. See [COMMITS.md.example](COMMITS.md.example) for a conventional commits template.

4. (Optional) Override the default model (`openai/gpt-5.6-luna`):
   ```bash
   export AICOMMIT_MODEL="anthropic/claude-sonnet-5"
   ```

## Usage

```bash
# Stage your changes
git add <files>

# Generate commit message and commit
aicommit

# Preview the commit message without committing
aicommit -n
aicommit --dry-run

# Pass additional git commit options
aicommit --no-verify

# One-liner: stage all, commit with AI message, and push
git add --all && aicommit && git push
```

## How it works

1. Checks for staged changes in the current git repository
2. Reads the diff of staged changes
3. Sends the diff to opencode AI along with your commit template (if exists)
4. Commits with the AI-generated message
5. Displays the full commit message

## Customization

Create `~/COMMITS.md` with your preferred commit message format and guidelines. The script will include this template in the prompt to the AI.

The script uses `openai/gpt-5.6-luna` by default — fastest, cheapest tier, enough for a one-line commit message. To use a different model, set `AICOMMIT_MODEL`.

Example for conventional commits - see [COMMITS.md.example](COMMITS.md.example).

## License

MIT
