# Simple Mac Setup Guide for Claude Desktop

## Step 1: Download Programs
1. Open Safari
2. Go to claude.ai and download Claude Desktop
3. Move Claude app to Applications folder

## Step 2: Get API Keys
You need two special passwords (called API keys):

### For Brave Search:
1. Go to brave.com/search/api
2. Click 'Get Started'
3. Create account (needs credit card but is free)
4. Click 'Add API Key'
5. Copy the key somewhere safe

### For GitHub:
1. Go to github.com
2. Click 'Sign Up'
3. Create account
4. Click your profile picture (top right)
5. Click 'Settings'
6. Click 'Developer Settings' (bottom left)
7. Click 'Personal access tokens'
8. Click 'Generate new token (Classic)'
9. Copy the key somewhere safe

## Step 3: Create Special File
1. Press Command + Space
2. Type 'Terminal' and press Enter
3. Copy and paste each line below (press Enter after each):

```
cd ~/Library/Application\ Support/Claude
```
```
nano claude_desktop_config.json
```

4. Copy this exactly (replace YOUR-KEYS with ones you saved):
```
{
  "mcpServers": {
    "brave-search": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-brave-search"],
      "env": {
        "BRAVE_API_KEY": "YOUR-BRAVE-KEY"
      }
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "YOUR-GITHUB-KEY"
      }
    }
  }
}
```

5. Press Control + X
6. Press Y
7. Press Enter

## Step 4: Final Setup
1. Copy and paste these two lines (press Enter after each):
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
(Type your computer password when asked)

```
brew install node
brew install nvm
```

2. Copy and paste both lines:
```
npx @modelcontextprotocol/server-brave-search
npx @modelcontextprotocol/server-github
```
(Type Y when asked)

## Step 5: Use Claude
1. Close Claude Desktop if it's open
2. Open Claude Desktop again
3. You're done!

Need help? Ask in GitHub issues or contact support.