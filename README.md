# Use multiple Github account in same environment
This topic provides a step-by-step guide to setting up host aliases for multiple GitHub accounts in a single environment. Using multiple Git accounts is a common practice in software development, as it helps separate work and personal projects, enhancing organization and security without increasing complexity

Topic
<ol type = "1">
    <li>Create or open your SSH config file</li>
    <li>Test the connection</li>
    <li>Basic Troubleshooting Tips</li>
</ol>

> Learning notes
>
> This section aims to give users a clearer understanding of configuring host aliases and offers basic troubleshooting for common errors encountered during Git operations

## Create or open your SSH config file
1. Refer to this url https://github.com/laoniu-meow/git-02-generate-key-configuration if you want to generate key for another GitHub account
2. Assume that you already have two GitHub accounts and have generated the corresponding SSH keys (e.g., stored in ~/.ssh/github)
3. I will use Linux commands to create the file as part of this setup
```bash
# 1. Navigate to .ssh folder and create a new file: config
cd ~/.ssh
touch config

# 2. Use Text Editor - nano, you can use any command editor you prefer
nano config

# Alternatively, you can use VS Code to open the .ssh/config file, but we encourage using Linux commands to build your knowledge and confidence with the CLI

# Quick tips:
# You can also open the file and edit it using a more efficient method, which follows the same logic as described in Step 3:
nano ~/.ssh/config      # navigate the file and open the file with text editor

# After you configure the config file, press Ctrl + 'E' then  press 'Y' and enter, you config file will be save the changes
```
4. In the config file we want to configure and define alias
```bash
# Account 1: Personal account
Host github.com-personal        # <- Host Name
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_personal     # <- Your private directory and key file where you stored

# Account 2: Work account
Host github.com-work            # <- Host Name
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_work         # <- Your private directory and key file where you stored
```
5. Remember to save after change the settings
- In command text editor, press Ctrl + 'E' then  press 'Y' and enter
- In VS Code editor, press Ctrl + 'S' or File -> select 'Save'

## Test the connection
Tip: Do you remember using this command in the previous guide to test the connection?
```bash
ssh -T git@github.com

# Output: Hi laomeowmeow! You've successfully authenticated, but GitHub does not provide shell access
```
‼️‼️‼️Now that you have set up two accounts and configured the config file, you can test the connection using the following command
```bash
ssh -T git@<hostname-in-config>

# Output: Hi laoniu-meow! You've successfully authenticated, but GitHub does not provide shell access
```

## Basic Troubleshooting tips
This is a common error, and many beginners are not aware of it when using multiple accounts, especially when performing a git clone to store a new repository locally