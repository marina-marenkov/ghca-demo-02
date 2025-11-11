# Quick Reference Guide

This quick reference provides handy commands, prompts, and tips for the OctoFit Tracker workshop.

## 🎯 GitHub Copilot Agent Mode Basics

### Activating Agent Mode

1. Open Copilot Chat (click Copilot icon or `Ctrl+Alt+I`)
2. Select **"Agent"** from the dropdown (not "Ask" or "Edit")
3. Type your prompt
4. Press Enter

### Agent Mode Best Practices

✅ **Do:**
- Be specific about what you want
- Provide context about your goal
- Ask follow-up questions
- Let agent mode fix its own errors
- Review changes before committing

❌ **Don't:**
- Give vague or ambiguous requests
- Interrupt agent mode while it's working
- Manually fix errors (let agent mode try first)
- Skip reviewing the changes made

## 💬 Common Prompts

### Getting Started

```
Please create and publish a new Git branch called build-octofit-app
```

```
Show me the current directory structure
```

```
What files are in the .github/instructions folder?
```

### Project Setup

```
Follow the OctoFit Tracker App structure instructions to create the directory layout
```

```
Create the Python virtual environment in octofit-tracker/backend/venv
```

```
Create requirements.txt file according to the instructions and install the dependencies
```

### Django Backend

```
Create a new Django project called octofit_tracker in the backend directory
```

```
Set up Django REST Framework according to the instructions
```

```
Create a Django app for user management with models, serializers, and views
```

```
Configure MongoDB connection in Django settings
```

### React Frontend

```
Create a new React app in the frontend directory using create-react-app
```

```
Install Bootstrap and configure it in the React app
```

```
Create a Dashboard component that displays user statistics
```

```
Set up React Router with routes for the main pages
```

### Git Operations

```
Show me what files have changed
```

```
Commit these changes with message "Add user authentication"
```

```
Push my changes to the remote branch
```

```
Create a pull request for my current branch
```

### Debugging

```
Why did that command fail?
```

```
The server isn't starting, what's wrong?
```

```
Fix the error in the last command you ran
```

```
Check if MongoDB is running
```

## 🔧 Useful Commands

### Python/Django

```bash
# Activate virtual environment
source octofit-tracker/backend/venv/bin/activate

# Install requirements
pip install -r octofit-tracker/backend/requirements.txt

# Create Django project
django-admin startproject octofit_tracker octofit-tracker/backend/

# Create Django app
python octofit-tracker/backend/manage.py startapp users

# Run migrations
python octofit-tracker/backend/manage.py makemigrations
python octofit-tracker/backend/manage.py migrate

# Create superuser
python octofit-tracker/backend/manage.py createsuperuser

# Run development server
python octofit-tracker/backend/manage.py runserver 0.0.0.0:8000
```

### Node.js/React

```bash
# Create React app
npx create-react-app octofit-tracker/frontend --use-npm

# Install dependencies
npm install --prefix octofit-tracker/frontend

# Install specific package
npm install bootstrap --prefix octofit-tracker/frontend

# Start development server
npm start --prefix octofit-tracker/frontend

# Build for production
npm run build --prefix octofit-tracker/frontend
```

### MongoDB

```bash
# Check if MongoDB is running
ps aux | grep mongod

# Start MongoDB (if needed)
sudo systemctl start mongod

# Stop MongoDB
sudo systemctl stop mongod

# MongoDB shell
mongosh

# Show databases
mongosh --eval "show dbs"

# Show collections in octofit_db
mongosh octofit_db --eval "show collections"
```

### Git

```bash
# Check status
git status

# View changes
git diff

# Stage all changes
git add .

# Commit changes
git commit -m "Your message"

# Push to remote
git push

# Create and switch to new branch
git checkout -b branch-name

# View branches
git branch -a

# View commit history
git log --oneline
```

### File Operations

```bash
# List files
ls -la

# View file contents
cat filename

# Create directory
mkdir -p path/to/directory

# Remove file
rm filename

# Remove directory
rm -rf directory

# Copy file
cp source destination

# Move/rename file
mv source destination
```

## 🗂️ Project Structure Reference

### Expected Directory Layout

```
octofit-tracker/
├── backend/
│   ├── venv/                      # Virtual environment
│   ├── octofit_tracker/           # Django project
│   │   ├── manage.py
│   │   ├── requirements.txt
│   │   ├── octofit_tracker/       # Settings
│   │   ├── users/                 # User app
│   │   ├── activities/            # Activities app
│   │   ├── teams/                 # Teams app
│   │   └── leaderboard/           # Leaderboard app
└── frontend/
    ├── node_modules/              # Node dependencies
    ├── public/
    ├── src/
    │   ├── components/
    │   ├── App.js
    │   └── index.js
    └── package.json
```

### Important Files

| File | Purpose |
|------|---------|
| `backend/requirements.txt` | Python dependencies |
| `backend/manage.py` | Django management script |
| `backend/octofit_tracker/settings.py` | Django configuration |
| `frontend/package.json` | Node.js dependencies |
| `frontend/src/App.js` | Main React component |

## 🎨 Copilot Slash Commands

Use these in Copilot Chat (both Chat and Agent mode):

| Command | Description |
|---------|-------------|
| `/explain` | Explain selected code |
| `/fix` | Suggest fixes for problems |
| `/tests` | Generate unit tests |
| `/help` | Get help with Copilot |
| `/clear` | Clear chat history |
| `/new` | Start new conversation |

## 🐛 Troubleshooting Quick Fixes

### Python Issues

**Problem**: Module not found
```bash
# Ensure virtual environment is activated
source octofit-tracker/backend/venv/bin/activate
# Reinstall requirements
pip install -r octofit-tracker/backend/requirements.txt
```

**Problem**: Django admin error
```bash
# Run migrations
python octofit-tracker/backend/manage.py migrate
```

### Node.js Issues

**Problem**: Package not found
```bash
# Reinstall dependencies
cd octofit-tracker/frontend && npm install
```

**Problem**: Port already in use
```bash
# Kill process on port 3000
lsof -ti:3000 | xargs kill -9
```

### MongoDB Issues

**Problem**: Connection refused
```bash
# Check if running
ps aux | grep mongod
# Start if not running
sudo systemctl start mongod
```

### Git Issues

**Problem**: Merge conflicts
```bash
# View conflicted files
git status
# Ask Copilot to help resolve
```

**Problem**: Uncommitted changes
```bash
# Stash changes
git stash
# Apply later
git stash pop
```

## 📝 Code Snippets

### Django Model Example

```python
from djongo import models

class Activity(models.Model):
    user = models.ForeignKey('users.User', on_delete=models.CASCADE)
    activity_type = models.CharField(max_length=50)
    duration = models.IntegerField()  # minutes
    points = models.IntegerField(default=0)
    date = models.DateTimeField(auto_now_add=True)
    
    class Meta:
        db_table = 'activities'
```

### Django Serializer Example

```python
from rest_framework import serializers
from .models import Activity

class ActivitySerializer(serializers.ModelSerializer):
    class Meta:
        model = Activity
        fields = ['id', 'user', 'activity_type', 'duration', 'points', 'date']
```

### Django View Example

```python
from rest_framework import viewsets
from .models import Activity
from .serializers import ActivitySerializer

class ActivityViewSet(viewsets.ModelViewSet):
    queryset = Activity.objects.all()
    serializer_class = ActivitySerializer
```

### React Component Example

```javascript
import React, { useState, useEffect } from 'react';

function Dashboard() {
  const [activities, setActivities] = useState([]);
  
  useEffect(() => {
    fetch('http://localhost:8000/api/activities/')
      .then(response => response.json())
      .then(data => setActivities(data));
  }, []);
  
  return (
    <div className="container">
      <h1>Dashboard</h1>
      {/* Display activities */}
    </div>
  );
}

export default Dashboard;
```

## 🔗 Quick Links

### Documentation
- [Main README](../README.md)
- [Setup Guide](SETUP.md)
- [Architecture](ARCHITECTURE.md)
- [Contributing](../CONTRIBUTING.md)

### Step-by-Step Guides
- [Step 1: Preparing](../.github/steps/1-preparing.md)
- [Step 2: Initial Setup](../.github/steps/2-application-initial-setup.md)
- [Step 3: Django Setup](../.github/steps/3-django-project-setup.md)
- [Step 4: Django REST](../.github/steps/4-setup-django-rest-framework.md)
- [Step 5: React Frontend](../.github/steps/5-setup-frontend-react-framework.md)
- [Step 6: Copilot on GitHub](../.github/steps/6-copilot-on-github.md)

### External Resources
- [GitHub Copilot Docs](https://docs.github.com/copilot)
- [Django Docs](https://docs.djangoproject.com)
- [React Docs](https://react.dev)
- [MongoDB Docs](https://docs.mongodb.com)

## 💡 Pro Tips

1. **Read error messages carefully** - They often tell you exactly what's wrong
2. **Ask Copilot to explain** - If you don't understand something, ask
3. **Commit often** - Small, frequent commits are easier to manage
4. **Let agent mode iterate** - It can fix its own mistakes
5. **Experiment** - Try different approaches and learn
6. **Take breaks** - Fresh eyes catch more errors
7. **Document decisions** - Add comments explaining why you did something
8. **Test incrementally** - Don't wait until the end to test
9. **Use version control** - Branch and experiment freely
10. **Have fun!** - You're learning cutting-edge AI-assisted development

## 🎯 Workshop Checklist

Use this to track your progress:

- [ ] Set up Codespace
- [ ] Verify Copilot agent mode works
- [ ] Create project structure
- [ ] Set up Python virtual environment
- [ ] Install Django and dependencies
- [ ] Create Django project
- [ ] Configure MongoDB
- [ ] Set up Django REST Framework
- [ ] Create backend apps (users, activities, teams, leaderboard)
- [ ] Create React app
- [ ] Install frontend dependencies
- [ ] Build React components
- [ ] Connect frontend to backend
- [ ] Test the application
- [ ] Create pull request
- [ ] Complete code review

---

**Need more help?** Check the [Setup Guide](SETUP.md) for detailed instructions or ask Copilot!
