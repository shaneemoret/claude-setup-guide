# The Friendly Guide to Setting Up Claude Desktop 😊

> Don't worry if you've never done anything like this before! We'll go through it step by step, and you can always ask Claude for help if you get stuck.

## Step 1: Opening Terminal
First, we need to open something called Terminal. Think of Terminal as your Mac's control panel - it's just a way to tell your Mac to do specific tasks. It might look a bit techy, but it's actually quite friendly once you get to know it!

1. Press the 🚀 Launchpad key on your keyboard (looks like a rocket)
2. Click the search bar at the top
3. Type 'Terminal'
4. Click the black square icon - that's Terminal! (It might look intimidating, but it's just waiting for your instructions)

## Step 2: Getting Your Special Keys (think of these as VIP passes)

### First VIP Pass (Brave Search):
1. Open Safari
2. Visit brave.com/search/api
3. Click 'Get Started'
4. Create an account (yes, it asks for a credit card, but it's free!)
5. Click 'Add API Key' - this creates your VIP pass
6. Copy your special key to Notes app

### Second VIP Pass (GitHub):
1. Visit github.com
2. Create an account (it's like making a social media profile, but for code)
3. Follow these clicks:
   - Your profile picture → Settings → Developer settings (at the bottom)
   - Personal access tokens → Generate new token (Classic)
4. Save this key in Notes too!

## Step 3: The Fun Part - Setting Up Claude!

### First magical command (copy/paste this into Terminal):
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
Don't worry about what this means - it's installing a helpful tool called Homebrew! When it asks for your password, type it in (the letters will be invisible - that's normal and kind of fun!)

### Now let's install some helpful tools:
```
brew install node
```
Then:
```
brew install nvm
```

### Time to create Claude's special folder:
```
cd ~/Library/Application\ Support/Claude
```

### Now we'll create Claude's settings file:
```
nano claude_desktop_config.json
```

### The Big Moment - Paste Your VIP Passes:
Copy this and replace YOUR-KEYS with the ones from your Notes:
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

### Save your work:
1. Press Control + X (like saving a document)
2. Press Y for 'Yes'
3. Press Enter to confirm

### Final Magic Spells:
```
npx @modelcontextprotocol/server-brave-search
```
When it asks, type 'y'
```
npx @modelcontextprotocol/server-github
```
Again, type 'y' when asked

## You're Almost There! 🎉
1. Close Claude Desktop if it's open
2. Open it again
3. Ta-da! You've done it!

### Got Stuck?
No worries at all! Here's what to do:
- Take a screenshot (Command + Shift + 4)
- Copy any error messages you see
- Share them with Claude - it's like having a tech-savvy friend who's always ready to help!

> Remember: Every tech expert started exactly where you are now. You're doing great! 🌟