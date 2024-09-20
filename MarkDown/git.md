# Git

# Table of Contents

1. [Basics](#basics)
2. [Best Practices](#best-practices)

# Basics

## Configuration

```
git config --global user.name "<your_name>"
git config --global user.email <your_email_address>

git config --global core.editor vim|"code --wait" # set default editor respectively, to vim, or vs-code
git config --global -e # opens the default editor

git config --global core.autocrlf input|true # respectively on Linux, or windows

git config --global color.ui true # make the output colorful
git config --global push.default current


git config --global diff.tool meld
```

## Useful commands

```
git <command> --help|-h 
```

## Getting Started

`git init`
`git clone url`

## Basics

```shell
git status
git add <file>
git add .
git commit -m "<meaningful_message>"
git commit # opens the default editor
git commit -a -m "<message>"
```

# Best Practices

## Good Practices for Commit Message Naming

Maintaining consistent, descriptive commit messages improves the readability of a project's history and helps future developers (and your future self!) understand what has changed. Below is a guide on how to name commits based on the type of action being performed, with examples from **deep learning projects**.

## Ideal Length for Commit Messages
- **Subject line (first line)**: Keep the subject line around **50 characters** or less. This ensures the commit message is concise but informative.
- **Body (optional)**: If more details are needed, add an explanation in the body. The body should be wrapped at **72 characters per line** to ensure good readability in most tools.

---

## 1. **New or Updated Feature**
- **Naming**: 
  - For adding a feature: `feat: Add [feature-name]`
  - For updating an existing feature: `feat: Update [feature-name]`
- **Explanation**: Use `feat` when **adding** a new feature or **updating** an existing one to indicate new functionality or modifications to it.
- **Example**: 
  - `feat: Add dropout layer to CNN model`
  - `feat: Update attention mechanism in Transformer for better accuracy`

---

## 2. **Bug Fix**
- **Naming**: `fix: Fix [issue]`
- **Explanation**: For **fixing** bugs, use `fix` to describe what issue was resolved.
- **Example**: 
  - `fix: Fix vanishing gradient issue in RNN training`
  - `fix: Correct data augmentation in image preprocessing pipeline`

---

## 3. **Refactoring**
- **Naming**: `refactor: Refactor [area/module]`
- **Explanation**: Use `refactor` when **restructuring or cleaning up** the code without changing its behavior.
- **Example**: 
  - `refactor: Refactor ResNet model to simplify architecture`
  - `refactor: Modularize data loading code for easier reuse`

---

## 4. **Style Changes**
- **Naming**: `style: Adjust [style-aspect]`
- **Explanation**: Use `style` for **formatting or stylistic changes** like linting, fixing whitespace, or non-functional changes.
- **Example**: 
  - `style: Fix PEP8 formatting issues in training script`
  - `style: Reformat code in LSTM implementation for readability`

---

## 5. **Performance Improvement**
- **Naming**: `perf: Improve [area/module] performance`
- **Explanation**: Use `perf` for **optimizing** the performance of a model, algorithm, or any other part of the system.
- **Example**: 
  - `perf: Optimize training loop for faster convergence`
  - `perf: Improve memory usage in multi-GPU training`

---

## 6. **Documentation Changes**
- **Naming**: `docs: Add [section] documentation` or `docs: Update [section] documentation`
- **Explanation**: Use `docs` when **adding** or **updating** project documentation, including README files or docstrings.
- **Example**: 
  - `docs: Add usage examples for Transformer model`
  - `docs: Update README with new model hyperparameters`

---

## 7. **Tests**
- **Naming**: `test: Add [specific-test]` or `test: Update [specific-test]`
- **Explanation**: Use `test` for **adding** or **updating** unit tests or integration tests in the codebase.
- **Example**: 
  - `test: Add unit tests for custom CNN layers`
  - `test: Update integration test for image classification pipeline`

---

## 8. **Chore**
- **Naming**: `chore: Add [task]` or `chore: Update [task]`
- **Explanation**: Use `chore` for **non-functional tasks** such as updating dependencies, build tools, or scripts.
- **Example**: 
  - `chore: Update PyTorch to version 1.9`
  - `chore: Add script to download pre-trained models`

---

## 9. **Merging Branches**
- **Naming**: `merge: Merge [source-branch] into [target-branch]`
- **Explanation**: Use `merge` when **merging** branches. Include both the source and target branches for clarity.
- **Example**: 
  - `merge: Merge feature/attention-layer into main`
  - `merge: Merge experimental/GAN-architecture into dev`

---

## 10. **Reverting Changes**
- **Naming**: `revert: Revert [commit-hash]`
- **Explanation**: Use `revert` when **undoing** a previous commit. Include the commit hash for reference.
- **Example**: 
  - `revert: Revert "feat: Add self-attention to Transformer" (commit abc123)`
  - `revert: Revert "perf: Optimize training loop" due to accuracy regression`

---

## 11. **Configuration Changes**
- **Naming**: `config: Add [configuration]` or `config: Update [configuration]`
- **Explanation**: Use `config` for **adding** or **updating** configuration files, CI/CD pipelines, or build settings.
- **Example**: 
  - `config: Update learning rate schedule in config.yaml`
  - `config: Add Docker configuration for multi-GPU training setup`

---

## General Guidelines:
1. **Use present tense**: Use present tense for your commits, e.g., "Add," "Fix," "Refactor," etc.
2. **Be concise**: Keep the message short but descriptive. The subject line should be around **50 characters** or less.
3. **Use tags consistently**: Always start with the appropriate tag (e.g., `feat`, `fix`, `refactor`, etc.) to quickly convey the type of change.
4. **Additional details in the body**: If more explanation is required, use the body of the commit message to provide further details. The body should be wrapped at **72 characters per line** for readability.

By following these naming conventions and guidelines, your commits will be more meaningful and easier to navigate, making version history clearer and more efficient for everyone involved in the project.

