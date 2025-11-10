# Contributing to MyDbPortal Agent

First off, thank you for considering contributing! We welcome any help, from reporting a bug to submitting a feature. Every contribution helps make MyDbPortal Agent better.

This document provides a set of guidelines for contributing to the project. Please take a moment to review them to ensure a smooth and effective process for everyone.

## Code of Conduct

This project and everyone participating in it is governed by our [Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior.

## How Can I Contribute?

## Reporting Bugs and Suggesting Features

We use GitHub Issues to track bugs and feature requests.

- **To report a bug**, please open an issue with the "Bug Report" template and provide as much detail as possible.
- **To suggest a feature**, please open an issue with the "Feature Request" template and describe your idea.

### Your First Code Contribution

Unsure where to begin? Look for issues tagged with `good first issue` or `help wanted`. These are issues that we've identified as good starting points for new contributors.

## Development Workflow

Ready to contribute code? Here’s how to set up your environment and submit your changes.

1.  **Fork the Repository:**
    Click the "Fork" button at the top right of the [repository page](https://github.com/bonheur15/mydbportal-agent). This creates a copy of the project in your own GitHub account.

2.  **Clone Your Fork:**
    ```bash
    git clone https://github.com/YOUR_USERNAME/mydbportal-agent.git
    cd mydbportal-agent
    ```

3.  **Install Dependencies:**
    We use `bun` for package management.
    ```bash
    bun install
    ```

4.  **Create a New Branch:**
    Create a descriptive branch name for your changes.
    ```bash
    git checkout -b feature/your-awesome-feature
    ```
    Or for a bug fix:
    ```bash
    git checkout -b fix/bug-name
    ```

5.  **Make Your Changes:**
    Write your code! Make sure to follow the coding style and conventions.

6.  **Commit Your Changes:**
    We follow the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) specification. A good commit message is essential.

    **Format:** `type(scope): subject`

    - **type:** `feat` (new feature), `fix` (bug fix), `docs` (documentation), `style` (formatting), `refactor`, `test`, `chore` (build or tooling changes).
    - **scope (optional):** The part of the codebase you're changing (e.g., `agent`, `init-script`, `auth`).
    - **subject:** A short, imperative-tense description of the change.

    **Example:**
    ```bash
    git commit -m "feat(agent): add disk usage to stats endpoint"
    ```

7.  **Push to Your Fork:**
    ```bash
    git push origin feature/your-awesome-feature
    ```

8.  **Open a Pull Request:**
    Go to the original repository on GitHub and you'll see a prompt to open a pull request from your new branch. Fill out the pull request template with a clear description of your changes and a link to the issue it resolves.

## Coding Style

- **Language:** TypeScript
- **Simplicity:** Keep code simple, readable, and well-commented where necessary.

Thank you for your contribution!
