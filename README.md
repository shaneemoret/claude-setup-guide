# Claude Desktop Setup Guide: Connecting Brave Search and GitHub

## Prerequisites
1. Install Homebrew:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

2. Install Node and NVM:
```bash
brew install node
brew install nvm
```

3. Set up NVM:
```bash
mkdir ~/.nvm
echo 'export NVM_DIR="$HOME/.nvm"' >> ~/.zshrc
echo '[ -s "/opt/homebrew/opt/nvm/nvm.sh" ] && \. "/opt/homebrew/opt/nvm/nvm.sh"' >> ~/.zshrc
echo '[ -s "/opt/homebrew/opt/nvm/etc/bash_completion.d/nvm" ] && \. "/opt/homebrew/opt/nvm/etc/bash_completion.d/nvm"' >> ~/.zshrc
source ~/.zshrc
```

## Get API Keys

### Brave Search API
1. Go to brave.com/search/api/
2. Sign up for free tier (credit card required but free)
3. Click "Add API Key"
4. Copy your API key

### GitHub Token
1. Go to github.com and create account
2. Go to Settings > Developer Settings > Personal Access Tokens
3. Generate new token (Classic)
4. Select repo permissions
5. Copy the token

## Configuration Setup

1. Navigate to Claude config folder:
```bash
cd ~/Library/Application\ Support/Claude
```

2. Create config file:
```bash
nano claude_desktop_config.json
```

3. Add this configuration (replace with your API keys):
```json
{
  "mcpServers": {
    "brave-search": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-brave-search"],
      "env": {
        "BRAVE_API_KEY": "YOUR-BRAVE-API-KEY"
      }
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "YOUR-GITHUB-TOKEN" 
      }
    }
  }
}
```

4. Save file: Control + X, then Y, then Enter

## Install Servers
```bash
npx @modelcontextprotocol/server-brave-search
npx @modelcontextprotocol/server-github
```

## Final Steps
1. Restart Claude Desktop
2. You should see MCP tools available in the interface

## Security Notes
- Never share your API keys
- Treat tokens like passwords
- Review permissions before allowing actions

## Common Errors
- "BRAVE_API_KEY environment variable is required" - Check config file formatting
- "GITHUB_PERSONAL_ACCESS_TOKEN not set" - Verify token in config
- Node/NPM errors - Try updating npm: `npm install -g npm@latest`