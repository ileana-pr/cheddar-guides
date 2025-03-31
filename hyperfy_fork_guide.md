# Contributing to Hyperfy and Building Your Own Projects 🚀

Hey there! 👋 We're excited that you want to contribute to Hyperfy or build your own projects using our platform. This guide is here to help you navigate both paths smoothly. Whether you're here to contribute to the core project or create something amazing of your own, we've got you covered!

## Getting Started 🎯

1. First things first - fork our repository from [hyperfy-xyz/hyperfy](https://github.com/hyperfy-xyz/hyperfy)
2. Clone your fork locally:
   ```bash
   git clone https://github.com/YOUR_USERNAME/hyperfy.git
   cd hyperfy
   ```
3. Add our repository as upstream (this helps you stay in sync with us):
   ```bash
   git remote add upstream https://github.com/hyperfy-xyz/hyperfy.git
   ```

## Understanding Your Repository Structure 🔄

Your repository will have two remotes:
- `origin`: Your personal fork (where you push your changes)
- `upstream`: The main Hyperfy repository (where you get updates from us)

You can check your remotes anytime with:
```bash
git remote -v
```

## Our Branch Strategy 🌳

### The Main Branch
Think of `main` as your clean slate. We keep it pristine and in sync with our upstream repository. It's the perfect starting point for new features and fixes. Keep it updated with:
  ```bash
  git checkout main
  git fetch upstream
  git merge upstream/main
  ```

### Your Project Branch
Got a cool project in mind? Create a dedicated branch for it! This is your playground where you can experiment while still keeping the option to pull updates from us. When you want to update:
  ```bash
  git checkout my-project
  git merge main
  ```

### Feature Branches
When contributing to Hyperfy, create feature branches from `main`. We love clear naming - think `feature/awesome-new-thing` or `fix/that-pesky-bug`. Here's how it works:
  ```bash
  git checkout main
  git checkout -b feature/new-feature
  # Make your magic happen
  git push origin feature/new-feature
  # Create a PR and let us know what you've built!
  ```

## Managing Versions 📦

### For Your Projects
When you've got something awesome ready to share:
  ```bash
  git tag -a v1.0.0 -m "First stable release - it's alive!"
  git push origin v1.0.0
  ```
We recommend using semantic versioning (MAJOR.MINOR.PATCH) - it helps everyone understand what's changed!

### For Contributions
Keep your feature branches fresh and up-to-date with main. A clean history makes everyone happy! Don't forget to check our contribution guidelines - they're there to help make the process smooth for everyone.

## Our Best Practices 💡

1. **Keep It Focused**
   - One branch, one purpose
   - Small, meaningful commits are our jam

2. **Stay Updated**
   - Regular syncs with upstream keep things running smoothly
   - Update your project branch when you're ready for new features

3. **Document Everything**
   - We love good documentation! It helps everyone
   - Keep track of your changes and versions
   - Update READMEs as you go

4. **Test, Test, Test**
   - We can't stress this enough - test your changes thoroughly
   - Make sure everything works with both stable and latest versions

## Common Workflows 🛠️

### Contributing to Hyperfy
```bash
# Start fresh with our latest changes
git checkout main
git fetch upstream
git merge upstream/main

# Create your feature branch
git checkout -b feature/your-feature

# Work your magic
git add .
git commit -m "Added something awesome!"

# Share your work
git push origin feature/your-feature

# Create a PR and tell us about it!
```

### Building Your Project
```bash
# Create your project space
git checkout -b my-project

# Make it yours
git add .
git commit -m "Project-specific changes"

# When it's ready for the world
git tag -a v1.0.0 -m "First stable release"
git push origin v1.0.0
```

### Keeping Your Project Updated
```bash
# Get the latest from us
git checkout main
git fetch upstream
git merge upstream/main

# Update your project
git checkout my-project
git merge main

# Handle any conflicts (we've all been there!)
# Test everything thoroughly
```

## When Things Get Tricky 🤔

1. **Merge Conflicts**
   - Don't panic! Take your time to resolve conflicts
   - Test everything after resolving - we've got your back

2. **Branch Management**
   - If a branch gets messy, start fresh from main
   - Be careful with `git rebase` on shared branches

3. **Version Control**
   - Use `git revert` for shared history
   - Save `git reset` for your local branches

## Need More Help? 📚

We've got plenty of resources to help you out:
- [Hyperfy Documentation](https://hyperfy.how/) - Your go-to guide
- [GitHub Flow Guide](https://guides.github.com/introduction/flow/) - Git workflow best practices
- [Semantic Versioning](https://semver.org/) - Version numbering made simple
- [Git Best Practices](https://gist.github.com/luismts/495d982e8c5b1a0ced4a57cf3d93cf60) - Git wisdom from the pros

Remember, we're here to help! If you run into any issues or have questions, don't hesitate to reach out. Happy coding! 🚀 