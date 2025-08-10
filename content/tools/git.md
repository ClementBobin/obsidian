## Git

Git is an open source version control system that is widely used for tracking changes and collaborating on software development. It's especially powerful in distributed code projects where multiple developers are working on the same codebase.

## Installation

### Linux

Git can be easily installed on Linux systems using package managers. For Debian-based systems like Ubuntu, you can install it using:

```bash
sudo apt update sudo apt install git
```

### Windows

For Windows, you can download the Git installer from the [official Git website](https://git-scm.com/downloads) and run the executable.

### macOS

For macOS, you can use Homebrew to install Git. First, ensure you have Homebrew installed, then run:

```bash
brew install git
```
## Configuration

Git can be configured by the CLI using the `git config` command. For first configuration
it is necessary to configure at least the parameters `user.name` and `user.email`. This
can be done by the following commands:

```bash
git config --global user.name "MyFancyUser"
```

```bash
git config --global user.email "developer@mydomain.com"
```

## Using Git

The following commands can be helpful for working with `git`.

| git command                        | Comment                                                                                                                                        |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `git init`                         | Initialize a directory as git managed repository                                                                                               |
| `git clone <repo_url>`             | Clone a remote repository to your local client                                                                                                 |
| `git status`                       | Shows uncommited changes, new files etc.                                                                                                       |
| `git add <wildcard_or_filename>`   | Stage an updated / new file to the next commit                                                                                                 |
| `git rm <wildcard_or_filename>`    | Remove a file and stage the removal for the next commit                                                                                        |
| `git commit -m "<commit message">` | Commit staged changes under a new commit                                                                                                       |
| `git commit`                       | Will open an editor to write more descriptive commit messages.<br> See [here](https://cbea.ms/git-commit/) for a guide on good commit messages |
| `git checkout <branch_name>`       | Switch to another branch                                                                                                                       |
| `git branch`                       | Shows a list of existing branches                                                                                                              |
| `git branch <branch_name>`         | Creates a new branch (from the currently checked out branch)                                                                                   |
| `git merge <branch_name>`          | Merge changes from `branch_name` to the currently checked out branch                                                                           |
| `git push`                         | Push commited changes to the remote repository                                                                                                 |
| `git pull`                         | Pull current state from the remote repository to your local repo                                                                               |
### Staging Changes

To stage changes for the next commit, use `git add`:

```bash
git add <file_name>
```

You can also use wildcards or add all changes:


```bash
git add .
```
### Working with git-flow

Git-flow assists you by combining multiple steps of `git` commands to one `git-flow` command
which will do a workflow of steps. Although `git-flow` makes live easier in some cases,
it makes it also more complex sometimes and you need to execute some steps before or after using
a `git-flow` command as regular `git` command. (See below)

As an example, here is the comparison between the regular `git` commands and the appropriate
`git-flow` command for creating a release.

| git-flow command                                    | git command                                           |
| --------------------------------------------------- | ----------------------------------------------------- |
| `git-flow feature start <feature_name>`             | `git checkout -b feature/<feature_name> develop`      |
| `git-flow feature finish <feature_name> [--squash]` | `git checkout develop`                                |
|                                                     | `git merge [--squash] --no-ff feature/<feature_name>` |
|                                                     | `git branch -d feature/<feature_name>`                |

Another `git-flow` cheat sheet can be found [here](https://danielkummer.github.io/git-flow-cheatsheet/).

## Using git-crypt

Having secret or sensitive information in your git repository is never a good choice. But
sometimes it's necessary. Never push unencrypted data to your remote repository.

Git-crypt is a transparent encryption tool that works seamless with your Git repository. All sensitive
information is encrypted before pushed to the remote repository. Once you've unlocked the
repository locally, all data will be decrypted automatically when pulling from the remote
repo. This makes development with encrypted data effortless.

To install git-crypt, you can use your package manager of choice (e.g. `apt`):

```bash
sudo apt install git-crypt
```

To initialize a new repository with git-crypt, you can use `git-crypt init` when located in the
repository directory. An already encrypted git repository can be unlocked by `git-crypt unlock`.
This requires you to have either the repository encryption key in your GPG keychain, or that
your private GPG key has been added to the allowed keys in the repository. For more details, see the links below.

For more information, check out the official Github repository [here](https://github.com/AGWA/git-crypt).
A tutorial on git-crypt can be found [here](https://thedatabaseme.de/2022/04/13/lets-keep-this-our-secret-transparent-git-encryption-using-git-crypt/).

### Git Commit Options

When using `git commit`, you can utilize various options to control how your commits behave:

- `--amend`: This option allows you to amend the last commit. It's useful for making additional changes to the previous commit without creating a new commit.
    
- `--no-amend`: On the contrary, `--no-amend` prevents amending the last commit. It's handy when you want to keep the last commit as it is and create a new commit for your changes.
    

```bash
git commit --no-amend -m "This is a new commit"
```

### Git Merge Options

When performing a merge with `git merge`, you have some options to manage how the merge is executed:

- `--no-ff`: This option enforces a non-fast-forward merge. It creates a merge commit even if Git could perform a fast-forward merge, preserving the branch history.

```bash
git merge --no-ff <branch_name>
```

### Git Push Options

When pushing your changes to a remote repository with `git push`, you can use options like:

- `--force`: This option allows you to forcefully push your changes, even if it results in non-fast-forward updates. Use with caution, as it can overwrite changes in the remote repository.

```bash
git push --force
```

- `--dry-run`: This option is used to simulate a push, showing you what would be pushed without actually performing the push. It's a good way to check your changes before pushing.

```bash
git push --dry-run
```

### Git Pull Options

While pulling changes from a remote repository with `git pull`, you can include options like:

- `--rebase`: Instead of merging changes from the remote, this option rebases your local commits on top of the incoming changes. It helps maintain a linear commit history.

```bash
git pull --rebase
```

### Git Checkout Options

When using `git checkout` to switch branches or restore files, you can include options such as:

- `--b`: This option is used to create a new branch and switch to it in one step.

```bash
git checkout --b <new_branch>
```

- `--detach`: It detaches the HEAD, allowing you to inspect old commits or branches without making changes.

```bash
git checkout --detach <commit_hash>
```

### Git Reset Options

The `git reset` command allows you to reset the current HEAD to a specified state. Some useful options are:

- `--soft`: This option resets the HEAD to the specified commit but keeps the changes staged, allowing you to create a new commit.

```bash
git reset --soft <commit_hash>
```

- `--hard`: It resets the HEAD to the specified commit and discards all changes, making your working directory match the specified commit.

```bash
git reset --hard <commit_hash>
```

### Git Log Options

When using `git log` to view commit history, you can include options like:

- `--oneline`: This option condenses each commit to a single line, providing a more compact view of the commit history.

```bash
git log --oneline
```

- `--graph`: It displays a text-based graphical representation of the commit history.

```bash
git log --graph
```

### Git Stash Options

The `git stash` command allows you to save changes that haven't been committed yet. You can use options such as:

- `--list`: Lists the stashes that you currently have.

```bash
git stash --list
```

- `pop`: Removes and applies the latest stash.

```bash
git stash pop
```

### Git Merge Options

When using `git merge` to merge branches, you can include options like:

- `--no-ff`: This option ensures that a merge commit is always created, even if Git could perform a fast-forward merge.

```bash
git merge --no-ff <branch_to_merge>
```

- `--squash`: It condenses all the changes from a branch into a single commit when merging.

```bash
git merge --squash <branch_to_merge>
```

### Git Tag Options

Tags in Git are used to mark specific points in Git history. Some options for `git tag` are:

- `-a` or `--annotate`: This option creates an annotated tag, including a message for the tag.

```bash
git tag -a <tag_name> -m "Tagging version x.y.z"
```

- `-l` or `--list`: Lists tags.

```bash
git tag -l
```

### Git Remote Options

When managing remote repositories, you can use options with `git remote`:

- `-v` or `--verbose`: This option shows more information, including the URL of the remotes.

```bash
git remote -v
```

- `rename`: This renames a remote.

```bash
git remote rename <old_remote_name> <new_remote_name>
```

### Git Clean Options

`git clean` is used to remove untracked files from the working tree. Some options are:

- `-n` or `--dry-run`: This option shows what would be deleted without actually deleting anything.

```bash
git clean -n
```

- `-f` or `--force`: This option actually deletes the untracked files.

```bash
git clean -f
```

### Git Diff Options

The `git diff` command is used to show changes between commits, branches, etc. Some options are:

- `--stat`: This option provides a summary of changes.

```bash
git diff --stat
```

- `--name-only`: This option lists only the changed files.

```bash
git diff --name-only
```

These are just a few of the options available for various Git commands. Git provides a wide range of options to tailor your workflow to your specific needs. You can explore additional options by referring to the official Git documentation or by using the `git --help` command followed by the specific Git command to see its options and descriptions. If you have any more specific questions or need further details, feel free to ask!

## The `.git` Folder in Git Repositories

The `.git` folder is a core component of any Git repository. It holds all the metadata and objects that define the version control of your project. Understanding the contents and structure of this folder is crucial for Git users.

### Structure of `.git` Folder

The `.git` folder contains several subdirectories and files:

1. **branches**: This directory stores branch references.
    
2. **hooks**: Git allows you to place scripts in this directory to trigger actions at certain points in the Git workflow, like before or after commits.
    
3. **info**: Contains the global exclude file. Patterns in this file are ignored by Git.
    
4. **objects**: Stores all the content for your database. This is where all of the objects are stored - blobs (file content), trees (directory structures), and commits.
    
5. **refs**: Holds pointers to specific commits, like branch heads, tags, and more.
    
6. **config**: The repository-specific configuration file.
    
7. **description**: A simple text file describing the repository.
    
8. **HEAD**: Points to the branch you currently have checked out.
    
9. **index**: A binary file that holds a temporary staging area for changes that are to be committed.
    
10. **logs**: Contains reflogs, which store a history of changes in references (like branches).
    

### Important Files and Their Roles

- **config**: Configuration options for the repository.
    
- **HEAD**: Points to the branch you currently have checked out, or the specific commit if in a 'detached HEAD' state.
    
- **index**: The staging area, where changes are prepared to be committed.
    

### Subdirectories: `objects` and `refs`

- **objects**: The core of Git, storing all data in the database. It has subdirectories named with the first two characters of the SHA-1 hash for each object, containing the actual object files.
    
- **refs**: Contains references to commits. `refs/heads` stores branch references, `refs/tags` stores tag references, and `refs/remotes` stores references to remote repositories.
    

### Usage and Handling

You typically don't need to directly interact with the `.git` folder during normal usage. Git commands and tools manage the contents of this folder based on your actions (commits, branches, etc.).

However, in certain cases, understanding the structure and contents of the `.git` folder can be useful for advanced Git operations or troubleshooting.

## Conclusion

The `.git` folder is the backbone of every Git repository, storing essential metadata and objects. While it's not necessary to interact with this folder directly for routine Git usage, having a foundational understanding of its structure and contents can be beneficial for advanced Git operations and troubleshooting.

## The `.gitignore` File in Git

### Purpose

The `.gitignore` file is used to specify intentionally untracked files that Git should ignore. These files often include build artifacts, temporary files, IDE-specific files, and sensitive information like API keys or passwords.

### Location

The `.gitignore` file is typically placed at the root of your Git repository.

### Syntax

The `.gitignore` file uses a simple pattern matching syntax to specify files and directories to ignore. Some common patterns include:

- **Wildcards**: `*` (matches zero or more characters), `?` (matches a single character).
    
- **Negation**: `!` (negates a pattern).
    
- **Comments**: Lines starting with `#` are treated as comments.
    
- **Directory separator**: `/` is used to ignore files in a specific directory.
    

### Example `.gitignore` File

``` txt
# Ignore build artifacts 
build/  
# Ignore .env files 
.env  
# Ignore log files 
*.log  
# Ignore all .txt files in the logs directory 
logs/*.txt
```

### Usage

1. **Creating the File**: Create a new file named `.gitignore` at the root of your Git repository.
    
2. **Editing the File**: Add the file and directory patterns you want to ignore.
    
3. **Committing**: Commit the `.gitignore` file to apply the ignore rules to your repository.
    

### Important Points

- **Negation**: You can negate rules using `!`. For example, to ignore all files in a directory except a specific file:
    
```txt
directory/* !directory/important.txt
```
    
- **Global Ignore**: Git also supports a global `.gitignore` file (`~/.gitignore_global`), which applies to all Git repositories on your system.
    
- **Patterns Match Relative to `.gitignore`**: Patterns in a `.gitignore` file are matched relative to the location of the `.gitignore` file.
    
- **Comments and Blank Lines**: Comments start with `#`, and blank lines are ignored.
    

### Example Use Cases

- **Ignoring Compiled Code**: Ignore files generated during compilation.
    
- **Ignoring Dependencies**: Ignore dependencies installed via package managers.
    
- **Ignoring IDE/Editor Files**: Ignore project-specific settings or cache files created by your IDE or editor.
    
- **Ignoring Sensitive Information**: Ignore files containing sensitive data like passwords or API keys.
    

## Conclusion

The `.gitignore` file is a powerful tool for managing which files Git should ignore. By specifying patterns for files and directories, you can avoid unnecessary clutter and keep sensitive information out of your repository. Understanding how to use and configure `.gitignore` is essential for maintaining a clean and organized Git repository.