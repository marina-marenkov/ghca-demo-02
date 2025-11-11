# Build Applications with GitHub Copilot Agent Mode

<img src="https://octodex.github.com/images/Professortocat_v2.png" align="right" height="200px" />

Welcome to the **Build Applications with GitHub Copilot Agent Mode** workshop! This hands-on exercise will teach you how to leverage GitHub Copilot's agent mode to build a full-stack fitness tracking application called **OctoFit Tracker**.

## 🎯 About This Repository

This is a GitHub Skills workshop repository designed to help you learn GitHub Copilot agent mode through practical, hands-on experience. You'll build an OctoFit Tracker application from scratch using Copilot's AI-powered assistance.

### What is GitHub Copilot Agent Mode?

Copilot agent mode is an autonomous and dynamic AI collaborator that can:
- Create applications from scratch
- Refactor code across multiple files
- Write and run tests automatically
- Migrate legacy code to modern frameworks
- Generate documentation and integrate new libraries
- Orchestrate your entire development workflow

Unlike traditional code completion, agent mode operates autonomously by:
1. Determining relevant context and files to edit
2. Offering both code changes and terminal commands
3. Monitoring correctness and iterating to fix issues
4. Self-healing when errors occur

## 🏋️ What You'll Build

**OctoFit Tracker** is a fitness tracking application for Mergington High School that includes:

- 👤 User authentication and profiles
- 📊 Activity logging and tracking
- 👥 Team creation and management
- 🏆 Competitive leaderboards
- 💪 Personalized workout suggestions

### Technology Stack

- **Frontend**: React.js with Bootstrap
- **Backend**: Python with Django REST Framework
- **Database**: MongoDB
- **Development Environment**: GitHub Codespaces

## 🚀 Getting Started

### Prerequisites

- A GitHub account with GitHub Copilot access
- Basic familiarity with web development concepts
- No advanced coding skills required - Copilot will guide you!

### Quick Start

1. **Start the Exercise**: Click the button below to begin
   
   [![Go to Exercise](https://img.shields.io/badge/Go%20to%20Exercise-%E2%86%92-1f883d?style=for-the-badge&logo=github&labelColor=197935)](../../issues/1)

2. **Create a Codespace**: Follow the instructions in the first step to launch your development environment

3. **Follow Along**: Work through the step-by-step exercises with Copilot agent mode

## 📚 Repository Structure

```
.
├── .devcontainer/          # Codespaces configuration
├── .github/
│   ├── instructions/       # Custom instructions for Copilot agent mode
│   ├── prompts/           # Ready-to-use prompts for exercises
│   ├── steps/             # Step-by-step exercise guides
│   └── workflows/         # GitHub Actions workflows
├── docs/
│   └── octofit_story.md   # Background story and workshop overview
├── .gitignore             # Git ignore rules
├── LICENSE                # MIT License
└── README.md              # This file
```

### Key Files and Directories

- **`.github/instructions/`**: Contains custom instruction files that guide Copilot agent mode on how to structure and build the application
- **`.github/prompts/`**: Pre-written prompts for common tasks in the exercises
- **`.github/steps/`**: Detailed step-by-step guides for each exercise phase
- **`docs/octofit_story.md`**: The narrative behind the OctoFit Tracker application

## 📖 Workshop Structure

The workshop is organized into sequential steps:

1. **Preparing** - Set up GitHub Codespaces and understand Copilot agent mode
2. **Initial Setup** - Create directory structure and dependencies
3. **Django Project Setup** - Build the backend foundation
4. **Django REST Framework** - Create API endpoints
5. **React Frontend** - Build the user interface
6. **Copilot on GitHub** - Use Copilot for code review and PR management

Each step builds on the previous one, gradually constructing a complete application.

## 🎓 Learning Objectives

By completing this workshop, you will:

- ✅ Understand how GitHub Copilot agent mode works
- ✅ Learn to write effective prompts for AI-assisted development
- ✅ Build a full-stack web application with minimal manual coding
- ✅ Practice using Django REST Framework and React with Copilot
- ✅ Experience autonomous code generation, testing, and debugging
- ✅ Learn best practices for working with AI coding assistants

## 🔧 What Gets Created

During this workshop, you'll create:

```
octofit-tracker/
├── backend/
│   ├── venv/                    # Python virtual environment
│   ├── octofit_tracker/         # Django project
│   │   ├── manage.py
│   │   ├── requirements.txt
│   │   └── ...
└── frontend/                    # React application
    ├── src/
    ├── public/
    ├── package.json
    └── ...
```

**Note**: This repository is a template. The actual application code will be created during the exercises as you work with Copilot agent mode.

## 🤝 Contributing

This is a learning repository. If you find issues or have suggestions for improvements:

1. Check existing issues
2. Create a new issue describing your suggestion
3. For maintainers: See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔗 Additional Resources

- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)
- [GitHub Copilot Agent Mode Guide](https://code.visualstudio.com/docs/copilot/chat/chat-agent-mode)
- [Prompt Engineering for GitHub Copilot](https://docs.github.com/en/copilot/using-github-copilot/prompt-engineering-for-github-copilot)
- [GitHub Skills](https://skills.github.com/)
- [Mastering GitHub Copilot: When to use AI agent mode](https://github.blog/ai-and-ml/github-copilot/mastering-github-copilot-when-to-use-ai-agent-mode/)

## 💬 Support

- For questions about the exercises, check the step-by-step guides in `.github/steps/`
- For technical issues, open an issue in this repository
- For general Copilot questions, see the [official documentation](https://docs.github.com/en/copilot)

---

&copy; 2025 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

