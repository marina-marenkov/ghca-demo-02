# Setup Guide for OctoFit Tracker Workshop

This guide provides detailed setup instructions for the "Build Applications with GitHub Copilot Agent Mode" workshop.

## 📋 Prerequisites

### Required

1. **GitHub Account**
   - Free account or higher
   - Must have access to GitHub Copilot
   - Sign up at [github.com](https://github.com)

2. **GitHub Copilot Subscription**
   - Individual, Business, or Enterprise plan
   - Check access: [github.com/settings/copilot](https://github.com/settings/copilot)
   - Free trial available for eligible users

3. **GitHub Codespaces**
   - Included with all GitHub accounts
   - Free tier: 60 hours/month (2-core) or 30 hours/month (4-core)
   - Check quota: [github.com/settings/billing](https://github.com/settings/billing)

### Recommended Knowledge

- Basic understanding of web development concepts
- Familiarity with command line/terminal
- Basic Git knowledge (clone, commit, push)
- **No advanced coding required** - Copilot will assist you!

## 🚀 Getting Started

### Step 1: Start the Exercise

1. Navigate to the repository on GitHub
2. Click the "Go to Exercise" button in the README
3. This opens Issue #1 with the first step instructions

### Step 2: Create Your Codespace

1. In the exercise instructions, click the "Open in GitHub Codespaces" badge
2. Verify the repository is YOUR fork (not the original)
   - ✅ Correct: `your-username/ghca-demo-02`
   - ❌ Wrong: `skills/build-applications-w-copilot-agent-mode`
3. Click **Create Codespace**
4. Wait 2-3 minutes for the environment to load

### Step 3: Verify Your Environment

Once your Codespace loads:

#### Check VS Code Interface

- **Left Panel**: File explorer, search, source control
- **Bottom Panel**: Terminal, output, debug console
- **Right Panel** (optional): Copilot Chat

#### Open GitHub Copilot Chat

1. Click the Copilot icon at the top of VS Code (purple icon)
2. If prompted, accept the GitHub Copilot terms
3. Verify the chat panel opens successfully

#### Test Terminal Access

1. Press `Ctrl+J` (or `Cmd+J` on Mac) to open the terminal
2. Run: `python3 --version`
   - Should show Python 3.x
3. Run: `node --version`
   - Should show Node.js version
4. Run: `mongod --version`
   - Should show MongoDB version

## 🛠️ Environment Details

### What's Pre-installed

Your Codespace comes with:

- **Python 3.x**: For Django backend
- **Node.js & npm**: For React frontend
- **MongoDB**: For database
- **Git**: For version control
- **GitHub CLI**: For GitHub operations
- **VS Code**: As the IDE

### Configured Ports

The following ports are configured for the application:

- **3000**: React frontend (public)
- **8000**: Django backend (public)
- **27017**: MongoDB (private)

These are automatically forwarded when the services start.

### Directory Structure

After completing the exercises, your workspace will look like:

```
/workspaces/ghca-demo-02/
├── .devcontainer/
├── .github/
│   ├── instructions/
│   ├── prompts/
│   ├── steps/
│   └── workflows/
├── docs/
├── octofit-tracker/          # Created during exercises
│   ├── backend/
│   │   ├── venv/
│   │   ├── octofit_tracker/
│   │   └── requirements.txt
│   └── frontend/
│       ├── src/
│       ├── public/
│       └── package.json
├── .gitignore
├── LICENSE
└── README.md
```

## 🎯 Using GitHub Copilot Agent Mode

### Accessing Agent Mode

1. Open Copilot Chat (click Copilot icon or use keyboard shortcut)
2. In the chat input, select **"Agent"** from the dropdown
   - Not "Ask" or "Edit" - specifically "Agent"
3. Type or paste your prompt
4. Press Enter

### Agent Mode vs. Chat Mode

| Feature | Chat Mode | Agent Mode |
|---------|-----------|------------|
| Answers questions | ✅ Yes | ✅ Yes |
| Generates code | ✅ Yes | ✅ Yes |
| Executes commands | ❌ No | ✅ Yes |
| Modifies multiple files | Limited | ✅ Yes |
| Self-corrects errors | ❌ No | ✅ Yes |
| Creates file structure | Manual | ✅ Automatic |

### How Agent Mode Works

When you give agent mode a task:

1. **Analysis**: Determines what needs to be done
2. **Planning**: Creates a step-by-step plan
3. **Execution**: Runs commands and creates/modifies files
4. **Monitoring**: Checks if actions succeeded
5. **Iteration**: Fixes errors and retries if needed
6. **Completion**: Confirms when done

You'll see this cycle in action during the exercises!

## 💡 Working with the Workshop

### Following the Exercises

Each exercise step provides:

- **Context**: What you'll accomplish
- **Prompts**: Ready-to-use text for Copilot
- **Instructions**: What to do with Copilot's responses
- **Verification**: How to check your work

### Copy-Paste Prompts

Prompts in the exercises look like:

> ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=flat-square&logo=github%20copilot&labelColor=512a97&color=ecd8ff)
>
> ```prompt
> Your prompt text here
> ```

1. Copy the text from the code block
2. Paste into Copilot Chat (in Agent mode)
3. Review what Copilot suggests
4. Click "Continue" to execute

### Interacting with Agent Mode

Agent mode is conversational:

- **Ask clarifying questions**: If unsure, ask Copilot
- **Provide feedback**: Tell it if something isn't right
- **Request changes**: Ask it to modify its approach
- **Iterate**: Work back and forth until satisfied

Example conversation:
```
You: "Create the Django project structure"
Copilot: "I'll create the project. Should I use SQLite or MongoDB?"
You: "Use MongoDB as specified in the instructions"
Copilot: "Got it, creating with MongoDB configuration..."
```

### Monitoring Progress

Watch the terminal output as Copilot executes commands:

- **Green text**: Successful operations
- **Yellow text**: Warnings (usually okay)
- **Red text**: Errors (Copilot will try to fix)

### Committing Changes

After each exercise:

1. Review what Copilot created/changed
2. Stage changes: `git add .`
3. Commit: `git commit -m "Descriptive message"`
4. Push: `git push`

Or ask Copilot to do it:
```
Please commit these changes with message "Complete step 2" and push
```

## 🐛 Troubleshooting

### Copilot Not Responding

**Problem**: Chat doesn't respond or shows errors

**Solutions**:
1. Check your Copilot subscription is active
2. Reload the VS Code window (`Cmd/Ctrl+R`)
3. Sign out and back into GitHub in VS Code
4. Verify network connection

### Agent Mode Not Available

**Problem**: Only see "Ask" and "Edit" options

**Solutions**:
1. Update VS Code and Copilot extensions
2. Restart the Codespace
3. Check that Copilot Chat extension is enabled

### Commands Fail

**Problem**: Copilot's commands return errors

**Solutions**:
1. Let agent mode attempt to fix (it usually will)
2. Check if you're in the right directory
3. Verify dependencies are installed
4. Ask Copilot: "Why did that command fail?"

### Port Not Accessible

**Problem**: Can't access app on port 3000 or 8000

**Solutions**:
1. Check the "Ports" tab in VS Code (bottom panel)
2. Ensure port visibility is set to "Public"
3. Wait for service to fully start
4. Check service logs in terminal

### MongoDB Connection Issues

**Problem**: Django can't connect to MongoDB

**Solutions**:
1. Verify MongoDB is running: `ps aux | grep mongod`
2. Start if needed: `sudo systemctl start mongod`
3. Check connection string in Django settings
4. Ask Copilot to fix the configuration

## 💾 Saving Your Work

### Automatic Saves

- **File edits**: Auto-saved in VS Code
- **Codespace state**: Saved when you close
- **Git commits**: Must be done manually (or via Copilot)

### Pausing and Resuming

You can close your Codespace anytime:

1. Changes are automatically saved
2. Next time you open, you'll be where you left off
3. Running processes will need to be restarted

### Best Practices

- **Commit often**: After each completed step
- **Push regularly**: Don't lose work if Codespace is deleted
- **Use branches**: Keep experimental work separate
- **Document decisions**: Add comments explaining choices

## 📞 Getting Help

### During the Workshop

1. **Read error messages**: Often contain the solution
2. **Ask Copilot**: "How do I fix this error?"
3. **Check the instructions**: In `.github/steps/`
4. **Review documentation**: In `docs/` folder

### Additional Resources

- **GitHub Copilot Docs**: [docs.github.com/copilot](https://docs.github.com/copilot)
- **VS Code Docs**: [code.visualstudio.com/docs](https://code.visualstudio.com/docs)
- **Django Docs**: [docs.djangoproject.com](https://docs.djangoproject.com)
- **React Docs**: [react.dev](https://react.dev)

### Still Stuck?

- Open an issue in the repository
- Check existing issues for similar problems
- Reach out to GitHub Support for Copilot issues

## ⏭️ Next Steps

Once your environment is set up:

1. Return to Issue #1 in your repository
2. Follow the step-by-step instructions
3. Use Copilot agent mode to build the application
4. Learn, experiment, and have fun!

---

**Ready to start building?** Head back to the [main README](../README.md) and begin your first exercise! 🚀
