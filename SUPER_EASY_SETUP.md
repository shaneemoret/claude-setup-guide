# Super Easy Claude Desktop Setup Guide for Mac

❗ If you run into problems at any step, take a screenshot (Command + Shift + 4) or copy any error messages. You can share these with Claude Desktop for help!

## Step 1: Opening Terminal
1. On your keyboard, press the Launchpad key (looks like a rocket 🚀)
2. At the top of your screen, click the search bar
3. Type 'Terminal'
4. Click the black box icon with 'Terminal' underneath

## Step 2: Getting Your Special Keys

### First Key (Brave Search):
1. Open Safari
2. Go to brave.com/search/api
3. Click the blue 'Get Started' button
4. Create an account (needs credit card but won't charge you)
5. Look for 'API Keys' on the left
6. Click 'Add API Key' (top right)
7. Copy the key (it looks like random letters/numbers)
8. Save it in Notes app for now

### Second Key (GitHub):
1. In Safari, go to github.com
2. Click 'Sign Up' (top right)
3. Create your account
4. Click the circle with your picture (top right)
5. Click 'Settings'
6. Scroll ALL the way down
7. Click 'Developer settings' (left side)
8. Click 'Personal access tokens'
9. Click 'Generate new token (Classic)'
10. Copy the key
11. Save it in Notes app too

## Step 3: Setting Up Claude

### First, copy/paste this EXACTLY into Terminal:
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
- Press Enter
- Type your Mac password when asked (you won't see the letters as you type)
- Wait until it's done

### Next, copy/paste these:
```
brew install node
```
Press Enter, then:
```
brew install nvm
```
Press Enter

### Now go to Claude's special folder:
```
cd ~/Library/Application\ Support/Claude
```
Press Enter

### Create Claude's settings file:
```
nano claude_desktop_config.json
```
Press Enter

### Copy this EXACTLY (replace YOUR-KEYS with the ones from your Notes app):
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

### Save the file:
1. Press Control + X
2. Press Y key
3. Press Enter key

### Last step! Copy/paste these:
```
npx @modelcontextprotocol/server-brave-search
```
Press Enter, type 'y' if asked
```
npx @modelcontextprotocol/server-github
```
Press Enter, type 'y' if asked

## Step 4: Start Using Claude!
1. If Claude Desktop is open, close it
2. Open Claude Desktop again
3. You're done! 🎉

### Need Help?
- Copy any error messages you see
- Take screenshots (Command + Shift + 4) of any problems
- Share these with Claude Desktop
- Claude can help fix any issues!
