## Overview
The session introduces the fundamentals of DevOps, its role in the software development lifecycle (SDLC), the responsibilities of a DevOps engineer, and the importance of automation through tools like Git, Jenkins, Docker, and Kubernetes. It also includes a practical lab on setting up Git for version control and integrating it with GitHub using SSH authentication. The documentation is divided into theoretical concepts and step-by-step practical instructions to ensure all aspects are covered comprehensively.

## Theoretical Concepts

### 1. Introduction to DevOps
- **Definition**: DevOps is a methodology that integrates **Development (Dev)** and **Operations (Ops)** to streamline the SDLC, automating processes from code development to production deployment.
- **Purpose**: Enhances collaboration between development and operations teams, ensuring efficient software delivery through automation.
- **Core Idea**: The common element is **code**. Developers write code, and operations teams deploy it in production.
- **Objective**: Automate the SDLC to facilitate continuous integration, testing, packaging, release, and deployment.

### 2. Software Development Lifecycle (SDLC)
- **Definition**: SDLC is the process of developing, testing, packaging, releasing, and deploying software.
- **Key Phases**:
  1. **Code Development**: Developers write code for new products, features, or issue fixes.
  2. **Packaging**: Code is converted into a deployable package (e.g., APK for Android, MSI for Windows, RPM for Red Hat, JAR for Java, Wheel for Python).
  3. **Testing**: Packages are tested for functionality and reliability.
  4. **Release**: Tested packages are released to platforms (e.g., Google Play Store).
  5. **Deployment**: Operations teams deploy packages in production environments.
- **DevOps Role**: Automates these phases to reduce manual effort and improve efficiency.

### 3. Why Developers Write Code
- Developers write code for three primary reasons:
  1. **New Product Development**: Creating new software products.
  2. **Fixing Issues**: Addressing bugs or issues in existing software.
  3. **Adding New Features**: Enhancing software with additional functionality.
- Code is written to meet specific requirements, initiating the DevOps process.

### 4. Packaging in Software Development
- **Purpose**: End users interact with packages, not raw code. Packages are created from code for distribution and installation.
- **Examples of Packages**:
  - **Android**: APK (Android Package) for Play Store.
  - **Windows**: MSI (Microsoft Installer) or EXE.
  - **Red Hat**: RPM (Red Hat Package Manager).
  - **Java**: JAR (Java Archive).
  - **Python**: Wheel files.
- **Packaging Process**:
  - Code is transformed into a package using specific build tools (e.g., Android build tools for APKs).
  - Packages are tested and released to platforms for end-user installation.
- **End-User Interaction**: Users install packages (e.g., WhatsApp APK) without interacting with the underlying code.

### 5. DevOps Methodology
- **Journey**: DevOps spans from code creation by developers to deployment by operations.
- **Automation**: Automates SDLC phases to ensure seamless transitions.
- **Key Tools**:
  - **Git**: Version control and code management.
  - **Jenkins**: Automates CI-CD pipelines.
  - **Docker**: Containerization for consistent environments.
  - **Kubernetes**: Container orchestration for scaling and management.
  - **AWS Tools**: AWS CodeBuild, CodeCommit (retired for new customers), and CodePipeline for cloud-based DevOps.
- **CI-CD Pipeline**:
  - **Continuous Integration (CI)**: Involves integrating code changes, testing, and packaging continuously.
  - **Continuous Deployment (CD)**: Deploys tested packages to production and monitors performance.
- **Role of a DevOps Engineer**:
  - Does **not** write application code or test cases.
  - Focuses on **automating SDLC** by writing CI-CD pipelines.
  - Responsibilities include:
    - Cloning code from repositories (e.g., GitHub).
    - Creating packages using specified tools.
    - Running tests provided by developers.
    - Releasing and deploying packages to production.
  - Writes automation scripts to control the flow from code check-in to deployment.

### 6. Agile Methodology
- **Definition**: Agile is a flexible software development approach that allows teams to adapt to changes at any SDLC stage.
- **Contrast with Waterfall Model**:
  - **Waterfall**: Linear model where each phase (e.g., design, coding, testing) must complete before the next, with no reverse flow.
  - **Agile**: Supports iterative changes, allowing modifications to architecture or code post-planning.
- **Key Principle**: Flexibility to accept incremental changes at any time, enhancing adaptability.

### 7. DevOps and Cloud Engineering
- **Relevance**: Cloud engineers benefit from DevOps knowledge as tools like Jenkins, Docker, and Kubernetes are cloud-agnostic and widely used.
- **Tool Dependency**: DevOps relies heavily on tools, not just cultural practices, to automate processes.

### 8. Practical Learning Path
- The session emphasizes learning DevOps basics, starting with Linux fundamentals.
- Upcoming topics include:
  - Detailed CI-CD pipeline implementation.
  - Hands-on labs with Git, Jenkins, Docker, and Kubernetes.
- Resources:
  - Scripts and screenshots (e.g., whiteboard content) to be shared.
  - Session recordings available for review.

## Practical Steps: Git Version Control Setup

The following steps outline the hands-on lab for setting up Git, initializing a repository, tracking and committing files, and pushing code to GitHub using SSH authentication. These steps were performed on a Linux-based AWS EC2 instance (Ubuntu or Amazon Linux).

### Prerequisites
- **Environment**: Linux machine (e.g., Ubuntu or Amazon Linux) on an AWS EC2 instance.
- **Git Installation**:
  - Ubuntu: `sudo apt-get update && sudo apt-get install git`
  - Amazon Linux: `sudo yum install git`
- **GitHub Account**: Required for remote repository creation and SSH key setup.
- **Tools**: SSH client (e.g., EC2 Instance Connect or PuTTY) for accessing the EC2 instance.

### Step-by-Step Instructions

#### Step 1: Create a Directory for the Git Repository
Create a working directory to initialize as a Git repository.

1. **Create a directory**:
   ```bash
   mkdir test
   ```
   - Creates a directory named `test` to serve as the local Git repository.

2. **Navigate to the directory**:
   ```bash
   cd test
   ```
   - Changes the current working directory to `test`.

#### Step 2: Check Git Status (Pre-Initialization)
Verify that the directory is not yet a Git repository.

1. **Run Git status**:
   ```bash
   git status
   ```
   - Expected output: `fatal: not a git repository (or any of the parent directories): .git`
   - Indicates the directory is not yet initialized as a Git repository.

2. **List hidden files**:
   ```bash
   ls -la
   ```
   - Checks for the `.git` subdirectory, which should not exist at this stage.

#### Step 3: Initialize the Git Repository
Initialize the directory as a Git repository to enable version control.

1. **Initialize Git**:
   ```bash
   git init
   ```
   - Initializes the `test` directory as a Git repository, creating a `.git` subdirectory.

2. **Verify initialization**:
   ```bash
   ls -la
   ```
   - Confirms the presence of the `.git` subdirectory.

3. **Check Git status**:
   ```bash
   git status
   ```
   - Expected output: `On branch master, No commits yet, nothing to commit`
   - Confirms the directory is now a Git repository.

#### Step 4: Configure Git User Details
Set up user information for Git to record authorship of changes.

1. **Set username**:
   ```bash
   git config --global user.name "Your Name"
   ```
   - Configures the username globally. Replace `"Your Name"` with your actual name.

2. **Set email**:
   ```bash
   git config --global user.email "your.email@example.com"
   ```
   - Configures the email address globally, preferably the email linked to your GitHub account.
   - Note: This is a one-time setup per system.

#### Step 5: Create and Track a File
Create a file and enable Git to track it.

1. **Create a file**:
   ```bash
   touch code
   ```
   - Creates an empty file named `code` in the `test` directory.

2. **Check Git status**:
   ```bash
   git status
   ```
   - Expected output: Lists `code` as an untracked file with a message like `Untracked files: (use "git add <file>..." to include in what will be committed)`.

3. **Stage the file**:
   ```bash
   git add code
   ```
   - Adds the `code` file to the staging area for tracking.

4. **Verify staging**:
   ```bash
   git status
   ```
   - Expected output: Shows `code` under `Changes to be committed`.

#### Step 6: Commit Changes
Record the staged changes as a version.

1. **Commit the file**:
   ```bash
   git commit -m "Initial commit"
   ```
   - Commits the staged `code` file with a descriptive message. The `-m` flag is mandatory.

2. **Check Git status**:
   ```bash
   git status
   ```
   - Expected output: `nothing to commit, working tree clean`.

3. **View commit history**:
   ```bash
   git log
   ```
   - Displays the commit ID, author, email, timestamp, and message (`Initial commit`).

4. **View reference log**:
   ```bash
   git reflog
   ```
   - Shows a summary of commit IDs and actions (e.g., `commit (initial)`).

#### Step 7: Modify a File and Track Changes
Modify a file to demonstrate version control.

1. **Edit the file**:
   ```bash
   vi code
   ```
   - Opens the `code` file in VI editor. Add a line, e.g., `date`, then save and exit (`:wq`).

2. **Check Git status**:
   ```bash
   git status
   ```
   - Expected output: Shows `code` as modified under `Changes not staged for commit`.

3. **Stage the modified file**:
   ```bash
   git add code
   ```
   - Stages the modified `code` file.

4. **Commit the changes**:
   ```bash
   git commit -m "Added date command"
   ```
   - Commits the changes with a message.

5. **View commit history**:
   ```bash
   git log
   ```
   - Shows two commits: the initial commit and the new commit.

6. **View reference log**:
   ```bash
   git reflog
   ```
   - Lists both commit IDs.

7. **Compare changes**:
   ```bash
   git diff <commit-id-1> <commit-id-2>
   ```
   - Replace `<commit-id-1>` and `<commit-id-2>` with commit IDs from `git log` or `git reflog`. Shows differences, e.g., the added `date` line.

#### Step 8: Set Up SSH Authentication for GitHub
Configure SSH authentication to push code to GitHub.

1. **Generate SSH key pair**:
   ```bash
   ssh-keygen -t rsa
   ```
   - Generates a private and public key pair. Press `Enter` to accept the default location (`~/.ssh/id_rsa`) and skip the passphrase (press `Enter` twice).

2. **View the public key**:
   ```bash
   cat ~/.ssh/id_rsa.pub
   ```
   - Displays the public key (starts with `ssh-rsa`). Copy the entire key, including `ssh-rsa` and the trailing email.

3. **Add the public key to GitHub**:
   - Log in to GitHub.
   - Navigate to **Settings** (top right) > **SSH and GPG keys** (left sidebar) > **New SSH key** or **Add SSH key**.
   - Paste the public key, name it (e.g., `EC2 Key`), and click **Add SSH key**.

#### Step 9: Create a GitHub Repository
Set up a remote repository on GitHub.

1. **Create a new repository**:
   - In GitHub, click **+** (top right) > **New repository**.
   - Name it (e.g., `first-test-batch`).
   - Use default settings (public, no README, no `.gitignore`, no license) and click **Create repository**.

2. **Copy the push commands**:
   - On the repository page, select the **SSH** tab.
   - Copy the three commands under **…or push an existing repository from the command line**, e.g.:
     ```bash
     git remote add origin git@github.com:username/first-test-batch.git
     git branch -M main
     git push -u origin main
     ```
   - Save these in a text editor.

#### Step 10: Push Code to GitHub
Link the local repository to GitHub and push the code.

1. **Navigate to the test directory**:
   ```bash
   cd ~/test
   ```
   - Ensures you are in the Git repository directory.

2. **Run the copied commands**:
   - Execute the three commands:
     ```bash
     git remote add origin git@github.com:username/first-test-batch.git
     ```
     - Links the local repository to the GitHub repository.
     ```bash
     git branch -M main
     ```
     - Renames the default branch to `main`.
     ```bash
     git push -u origin main
     ```
     - Pushes commits to the GitHub repository.

3. **Verify the push**:
   - Refresh the GitHub repository page.
   - Confirm the `code` file and commit history are visible.

### Troubleshooting
- **Git not installed**: Install using `sudo apt-get install git` (Ubuntu) or `sudo yum install git` (Amazon Linux).
- **Permission denied**: Use `sudo` for commands requiring elevated privileges.
- **Touch command issues**: Ensure you are in a Linux environment. If using Ubuntu, verify SSH access via `cat /etc/lsb-release`.
- **Git status error**: Run `cd test` to ensure you are in the Git repository directory.
- **SSH authentication failure**: Verify the public key is correctly added to GitHub and the private key is in `~/.ssh/id_rsa`.
- **Connection timeout**: Reconnect using AWS EC2 Instance Connect or an SSH client (e.g., PuTTY).
- **Syntax errors**:
  - For `git config`, ensure double hyphens: `git config --global user.name "Your Name"`.
  - For `git show`, use the correct commit ID from `git reflog`.
- **File not found**: Verify the current directory with `pwd` and navigate to `test` if needed.
- **Commit to staging**: Use `git revert <commit-id>` to undo a commit or `git rm --cached <file>` to unstage a file.

## Additional Notes
- **Version Control**: Git tracks file changes, creating commit IDs for each version. Use `git log` for commit history and `git diff` for comparing versions.
- **Staging Area**: The staging area holds files ready for committing (`git add` moves files here).
- **Commit IDs**: Unique identifiers for each commit, viewable via `git log` or `git reflog`.
- **AWS CodeCommit**: Retired for new customers, so Git and GitHub are used instead.
- **Learning Tips**:
  - Avoid blind copying from AI tools like ChatGPT. Understand the output to build expertise.
  - Practice commands in the provided labs to reinforce learning.
  - Use session recordings and shared screenshots for reference.
- **Market Relevance**:
  - Tools like Git, Jenkins, Docker, Kubernetes, Terraform, and AWS services (CodeBuild, CodePipeline) are in demand.
  - Skill requirements vary by experience (0–2 years: basic knowledge; 5–7 years: intermediate; 10+ years: SME-level).

## Conclusion
This documentation covers the theoretical foundations of DevOps, including its role in automating the SDLC, the CI-CD pipeline, and Agile methodology, alongside a detailed practical guide for using Git and GitHub. By following the steps, users can set up a local Git repository, manage version control, and integrate with GitHub securely. These skills are essential for DevOps engineers to automate software delivery processes effectively.
