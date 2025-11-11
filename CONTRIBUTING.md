# Contributing to Build Applications with GitHub Copilot Agent Mode

Thank you for your interest in contributing to this GitHub Skills workshop! This document provides guidelines for contributing to this educational repository.

## 🎯 About This Repository

This is an educational workshop repository designed to teach GitHub Copilot agent mode through hands-on exercises. It serves as a template that learners clone and work through step-by-step.

## 🤝 Types of Contributions

We welcome several types of contributions:

### 1. Bug Reports

If you find issues with the workshop:

- **Exercise Instructions**: Errors or unclear steps in `.github/steps/`
- **Custom Instructions**: Problems with `.github/instructions/` files
- **Documentation**: Typos, broken links, or confusing explanations
- **Technical Issues**: Problems with Codespaces configuration or dependencies

**How to Report**:
1. Search existing issues to avoid duplicates
2. Create a new issue with a clear title
3. Include:
   - What you expected to happen
   - What actually happened
   - Steps to reproduce (if applicable)
   - Screenshots (if helpful)

### 2. Documentation Improvements

Help make the workshop clearer:

- Fix typos or grammar
- Improve explanations
- Add examples or clarifications
- Update outdated information
- Enhance README or other docs

### 3. Workshop Content Enhancements

Suggestions for improving the learning experience:

- Additional exercises or challenges
- Alternative prompts that work better
- Improved custom instructions for Copilot
- New teaching examples

### 4. Technical Improvements

- Codespace configuration enhancements
- Dependency updates (with testing)
- GitHub Actions workflow improvements
- Development environment fixes

## 📝 Contribution Workflow

### For Small Changes (Documentation, Typos)

1. Fork the repository
2. Create a new branch: `git checkout -b fix/your-fix-name`
3. Make your changes
4. Commit with a clear message: `git commit -m "Fix: Correct typo in step 2 instructions"`
5. Push to your fork: `git push origin fix/your-fix-name`
6. Open a Pull Request with a clear description

### For Larger Changes (New Features, Content)

1. **Open an Issue First**: Discuss your proposed changes
2. Wait for feedback from maintainers
3. Once approved, follow the standard workflow above
4. Reference the issue in your PR: "Closes #123"

## ✅ Pull Request Guidelines

### Before Submitting

- [ ] Test your changes (especially for technical modifications)
- [ ] Update documentation if you changed functionality
- [ ] Ensure your changes work in GitHub Codespaces
- [ ] Check that markdown files render correctly
- [ ] Keep changes focused and atomic (one issue per PR)

### PR Description Should Include

- **What**: Brief description of the change
- **Why**: Reasoning behind the change
- **How**: Explanation of your approach (for complex changes)
- **Testing**: How you verified the changes work
- **Screenshots**: For UI or documentation changes

### Example PR Description

```markdown
## Fix incorrect prompt in Step 3

### What
Updated the Django project creation prompt to use correct directory path

### Why
The current prompt causes an error when Copilot tries to create the project in the wrong location

### How
Changed the path in `.github/prompts/create-django-project.prompt.md` from `backend/` to `octofit-tracker/backend/`

### Testing
- Tested in a fresh Codespace
- Verified Copilot agent mode successfully creates the project
- Confirmed no errors in subsequent steps
```

## 🎨 Style Guidelines

### Markdown Files

- Use ATX-style headers (`#` not underlines)
- Include blank lines around headers and lists
- Use code fences with language identifiers: ` ```python `
- Keep line length reasonable (80-120 characters)
- Use relative links for internal references

### Prompts and Instructions

- Write clear, action-oriented instructions
- Use consistent terminology
- Include examples where helpful
- Test prompts with Copilot before submitting

### Commit Messages

Follow conventional commit format:

- `feat:` New feature or exercise
- `fix:` Bug fix
- `docs:` Documentation changes
- `chore:` Maintenance tasks
- `refactor:` Code restructuring

Examples:
- `docs: Update README with clearer setup instructions`
- `fix: Correct Python dependencies in requirements.txt`
- `feat: Add bonus challenge to step 5`

## 🧪 Testing Your Changes

### For Documentation Changes

1. Preview markdown rendering (GitHub or local preview)
2. Check all links work
3. Verify images load correctly
4. Ensure formatting is consistent

### For Technical Changes

1. Create a new Codespace from your branch
2. Go through the affected exercises
3. Verify Copilot agent mode works as expected
4. Check that all commands execute successfully
5. Test both success and error scenarios

### For Instruction/Prompt Changes

1. Test with actual GitHub Copilot agent mode
2. Verify the output matches expectations
3. Check that learners won't get stuck
4. Ensure error messages are helpful

## 🔍 Review Process

1. **Automated Checks**: GitHub Actions will run basic validations
2. **Maintainer Review**: A maintainer will review your PR
3. **Feedback**: Address any requested changes
4. **Approval**: Once approved, a maintainer will merge

Please be patient - this is a community project and reviews may take a few days.

## 📋 Specific Areas Needing Help

We especially welcome contributions in:

- [ ] Improving exercise clarity based on learner feedback
- [ ] Adding troubleshooting tips for common issues
- [ ] Creating video walkthroughs or screenshots
- [ ] Testing with different Copilot models
- [ ] Updating dependencies to latest stable versions
- [ ] Adding accessibility improvements

## 🚫 What We Don't Accept

- Changes that fundamentally alter the workshop's learning objectives
- Adding external dependencies not essential for the exercises
- Modifying the core technology stack (React, Django, MongoDB)
- Changes without accompanying documentation updates
- Untested modifications to critical paths

## 📞 Getting Help

- **Questions about contributing**: Open a discussion or issue
- **Technical help**: See the main [README.md](README.md)
- **General Copilot questions**: Refer to [GitHub Copilot docs](https://docs.github.com/en/copilot)

## 🙏 Recognition

Contributors will be recognized in:
- GitHub's contributor list
- Release notes (for significant contributions)
- Our appreciation! 💚

## 📜 Code of Conduct

This project follows the [Contributor Covenant Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md). By participating, you agree to uphold this code.

## 📄 License

By contributing, you agree that your contributions will be licensed under the MIT License, the same license as this project.

---

Thank you for helping make this workshop better for everyone! 🚀
