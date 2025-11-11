# Frequently Asked Questions (FAQ)

Common questions and answers about the GitHub Copilot Agent Mode workshop.

## 📚 General Questions

### What is this workshop about?

This is a hands-on workshop where you learn to use GitHub Copilot's agent mode to build a full-stack fitness tracking application called OctoFit Tracker. You'll work with React, Django, and MongoDB—all with AI assistance.

### Do I need to know how to code?

Basic programming knowledge is helpful, but not required! The whole point is learning to work with Copilot agent mode, which can generate code for you. You should understand:
- Basic web concepts (frontend vs backend)
- How to use a terminal
- Basic Git operations

GitHub Copilot will help with the actual coding!

### How long does the workshop take?

Most people complete it in 2-4 hours, depending on:
- Your familiarity with the technologies
- How much you experiment and explore
- Whether you complete optional challenges

You can pause anytime and resume later—your Codespace saves your progress.

### Do I need to pay for anything?

You need:
- **GitHub Copilot subscription** - Free trial available for eligible users, or paid subscription
- **GitHub Codespaces** - Free tier (60 hours/month on 2-core) included with all accounts

The free tier is usually sufficient for this workshop.

### Can I keep the app I build?

Absolutely! The code you create is yours. You can:
- Continue developing it after the workshop
- Deploy it to a real server
- Use it as a portfolio project
- Extend it with new features

## 🛠️ Setup Questions

### How do I get GitHub Copilot?

1. Go to [github.com/features/copilot](https://github.com/features/copilot)
2. Click "Start free trial" or "Get Copilot"
3. Choose Individual, Business, or Enterprise
4. Follow the signup process
5. Install the VS Code extension

Free trials are available for verified students, teachers, and maintainers of popular open source projects.

### My Copilot isn't working. What should I do?

**Check these things:**
1. Is your subscription active? Visit [github.com/settings/copilot](https://github.com/settings/copilot)
2. Is the VS Code extension installed and enabled?
3. Are you signed into GitHub in VS Code?
4. Try reloading VS Code (`Ctrl/Cmd+R`)
5. Check the Copilot output panel for errors

Still not working? See [GitHub Copilot troubleshooting](https://docs.github.com/copilot/troubleshooting-github-copilot).

### Where's the "Agent" option in Copilot?

Make sure you have:
1. **Latest VS Code** - Update if needed
2. **Latest Copilot extensions** - Update both "GitHub Copilot" and "GitHub Copilot Chat"
3. **Agent mode enabled** - Check settings or update to a version that supports it

If you still don't see it, you might be using an older version that doesn't support agent mode yet.

### Can I use a local environment instead of Codespaces?

While possible, we strongly recommend Codespaces because:
- Pre-configured with all dependencies
- Consistent environment for all learners
- Works the same on any operating system
- No local setup required

If you must use local, ensure you have:
- Python 3.8+
- Node.js 16+
- MongoDB
- Git
- VS Code with Copilot

## 🤖 Copilot Agent Mode Questions

### What's the difference between Chat mode and Agent mode?

| Feature | Chat Mode | Agent Mode |
|---------|-----------|------------|
| Answers questions | ✅ | ✅ |
| Generates code | ✅ | ✅ |
| Runs commands | ❌ | ✅ |
| Edits multiple files | Limited | ✅ |
| Self-corrects | ❌ | ✅ |
| Autonomous | ❌ | ✅ |

**Use Chat mode for**: Quick questions, code explanations, suggestions

**Use Agent mode for**: Building features, refactoring, complex multi-step tasks

### How do I know if agent mode is working correctly?

You'll see agent mode:
1. Analyze your request
2. Show a plan or steps it will take
3. Ask for confirmation with "Continue" button
4. Execute commands in the terminal
5. Create/modify files
6. Report completion or errors

If you just get text responses without actions, you might be in Chat mode instead.

### Can I interrupt agent mode if it's doing something wrong?

Yes! You can:
- Stop execution before clicking "Continue"
- Give corrective feedback during execution
- Cancel with Ctrl+C in terminal if needed
- Undo changes with Git if already completed

Agent mode is conversational—feel free to course-correct.

### Agent mode made a mistake. What should I do?

1. **Let it try to fix itself first** - Agent mode can self-correct
2. **Provide specific feedback** - Tell it exactly what's wrong
3. **Ask questions** - "Why did you do it that way?"
4. **Manual fix as last resort** - Only if agent mode can't fix it

Example:
```
You: "The React component isn't rendering. Can you check why?"
Agent: "I see the issue - missing export statement. Let me fix it."
```

### How specific should my prompts be?

**Too vague:**
```
Make the app better
```

**Too specific:**
```
On line 47 of src/components/Dashboard.js, change the className 
from 'container' to 'container-fluid' and add a margin-top of 20px
```

**Just right:**
```
Update the Dashboard component to use a full-width container 
with some top margin for better spacing
```

**Rule of thumb:** Describe the goal, not the implementation details. Let agent mode figure out how.

## 🏗️ Technical Questions

### Why are we using MongoDB instead of PostgreSQL/MySQL?

Several reasons:
1. **Learning flexibility** - Schema-less design easier for beginners
2. **Modern stack** - Common in web development today
3. **JSON compatibility** - Natural fit with JavaScript/Python
4. **Workshop focus** - Less time on database design, more on Copilot

For production apps, the choice depends on your specific needs.

### Do I need to understand Django and React to do this workshop?

**Basic understanding helps**, but it's not required. The workshop teaches:
- How to use Copilot to build with these technologies
- Basic concepts as you go
- How to ask Copilot for explanations

You'll learn by doing! If you want to go deeper, check the documentation links provided.

### Can I use different technologies (Vue, Flask, etc.)?

The workshop is designed around React + Django + MongoDB. You could adapt it, but:
- ⚠️ The instructions won't match
- ⚠️ You'll need to modify prompts
- ⚠️ Less support available

If you're comfortable with that, go ahead and experiment!

### Where is my code? I don't see an octofit-tracker folder.

**That's expected!** This repository is a **template**. The actual application code gets created during the exercises as you work with Copilot.

After completing Step 2, you'll have:
```
octofit-tracker/
├── backend/
└── frontend/
```

### The ports aren't accessible. How do I fix this?

1. Check the "Ports" tab in VS Code (bottom panel)
2. Ensure ports 3000 and 8000 are listed
3. Set visibility to "Public" if they're private
4. Wait for services to fully start (check terminal output)
5. Click the "Open in Browser" icon

If still not working, restart the servers.

## 🐛 Common Problems

### "Permission denied" errors

**In Codespaces:**
```bash
# Use sudo for system operations
sudo systemctl start mongod

# Don't need sudo for project files
python manage.py runserver
```

**For virtual environment:**
```bash
# Make sure you're in the right directory
cd /workspaces/ghca-demo-02
source octofit-tracker/backend/venv/bin/activate
```

### "Module not found" errors

**Python:**
```bash
# Activate virtual environment first
source octofit-tracker/backend/venv/bin/activate
# Then install
pip install -r octofit-tracker/backend/requirements.txt
```

**Node.js:**
```bash
# Make sure you're in the right directory
cd octofit-tracker/frontend
npm install
```

### MongoDB connection errors

**Check if running:**
```bash
ps aux | grep mongod
```

**Start if needed:**
```bash
sudo systemctl start mongod
```

**Verify in Django settings:**
```python
DATABASES = {
    'default': {
        'ENGINE': 'djongo',
        'NAME': 'octofit_db',
        'CLIENT': {
            'host': 'localhost',
            'port': 27017,
        }
    }
}
```

### React app shows blank page

**Check console:**
1. Open browser DevTools (F12)
2. Look for errors in Console tab
3. Ask Copilot to fix the specific error

**Common causes:**
- Missing imports
- Syntax errors
- API connection issues
- Port not forwarded

### Django admin isn't working

**Create superuser:**
```bash
python octofit-tracker/backend/manage.py createsuperuser
```

**Run migrations:**
```bash
python octofit-tracker/backend/manage.py migrate
```

## 📝 Workshop Process Questions

### Do I have to follow the steps exactly?

The steps provide a guided path, but you can:
- Take detours to explore
- Try alternative approaches
- Add extra features
- Skip optional parts

Just understand that support is best for the standard path.

### Can I work with a team?

Absolutely! Team learning is great. You can:
- Pair program in the same Codespace
- Each build your own and compare
- Help each other troubleshoot
- Share interesting prompts you discover

### What if I get stuck?

Try this process:
1. **Read error messages** - They often tell you the fix
2. **Ask Copilot** - "Why did this fail? How do I fix it?"
3. **Check documentation** - Especially the step files
4. **Search existing issues** - Someone might have had the same problem
5. **Ask for help** - Create an issue with details

### How do I know if I'm doing it right?

After each step, the workshop instructions have verification steps. Generally:
- ✅ No errors in terminal
- ✅ Files created as expected
- ✅ Services start successfully
- ✅ Can access application in browser

Don't worry about perfection—learning is the goal!

## 🎓 After the Workshop

### What should I learn next?

Great follow-ups:
1. **Deploy your app** - Learn Heroku, AWS, or Vercel
2. **Add features** - Authentication, real-time updates, mobile app
3. **Learn testing** - Unit tests, integration tests, E2E tests
4. **Other GitHub Skills** - [skills.github.com](https://skills.github.com)
5. **Advanced Copilot** - Explore different models and modes

### Can I get a certificate?

This workshop doesn't offer a certificate, but you can:
- Add the project to your portfolio
- Share on LinkedIn/Twitter
- Include in your resume
- Use as a talking point in interviews

### How can I help improve this workshop?

We love contributions! You can:
- Report bugs or unclear instructions
- Suggest improvements
- Add examples or tips
- Help other learners in issues
- Share your experience

See [CONTRIBUTING.md](../CONTRIBUTING.md) for details.

### Where can I find more Copilot resources?

- [GitHub Copilot Documentation](https://docs.github.com/copilot)
- [Copilot Blog Posts](https://github.blog/tag/github-copilot/)
- [GitHub Skills](https://skills.github.com)
- [Copilot Community Discussions](https://github.com/community/community/discussions/categories/copilot)

## 🆘 Still Have Questions?

- **Check the documentation**: [README](../README.md), [Setup Guide](SETUP.md), [Architecture](ARCHITECTURE.md)
- **Search issues**: Someone might have asked already
- **Create an issue**: We're here to help!
- **GitHub Support**: For billing or account questions

---

**Happy building with GitHub Copilot!** 🚀
