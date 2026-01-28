[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/ekbAGxBG)
# Ruby on Rails development environment setup (Windows WSL)

**Time Estimate**: 3-4 hours
**Goal**: Transform your computer into a powerful workshop where you can build the "Island Formulator" app. By the end of this guide, you'll have a professional-grade Linux environment running on your Windows machine, fully connected to GitHub via SSH.

---

Here's how this assignment is structured:

### How You Got Here
1. Your instructor shared a **GitHub Classroom assignment link**
2. You clicked the link and GitHub automatically created a **personal copy** of this assignment repository for you (named something like `week0-environment-setup-yourusername`)
3. You cloned this repository to your computer using: `git clone git@github.com:classname/week0-environment-setup-yourusername.git`
4. This README.md file contains all the setup instructions you need to follow

### How to Submit This Assignment
After completing all the setup steps in this tutorial, you will:
1. Create a test Rails app called `workshop_test` **inside this assignment repository**
2. Commit the generated Rails code
3. Push to GitHub - that's your submission!

**Think of it like a homework folder**: Your instructor gave you a folder (this repo), you do the work inside it (create the Rails app), then you hand it back in (git push). Your instructor can then check your folder to verify your setup is working correctly.

Let's get started! 🚀

---

## Welcome, Future Developer! 🇯🇲

Welcome to the Island Formulator project! Before we start building our inventory management app for natural hair and skincare creators, we need to set up your "digital workshop."

Think of this like setting up a kitchen before you start cooking a big Sunday dinner. You need your stove (Ruby), your recipes (Rails), your pantry (PostgreSQL), and your utensils (VS Code). 

**Important Note for this Cohort**: We are focusing on **WSL (Windows Subsystem for Linux)**. Most professional Rails development happens on Linux or Mac. Since you are on Windows, WSL gives you the best of both worlds: the Windows apps you love and the powerful Linux environment required for modern web development.

---

## Understanding Your New Tools

Before we dive into the installation, let's understand the "why" behind each tool. Knowing how they fit together will make you a much more effective developer.

### 1. WSL: Your Linux Powerhouse 🐧
Windows is great for many things, but the world of web development—especially Ruby on Rails—is built on Linux. WSL (Windows Subsystem for Linux) is a layer that lets you run a full Linux operating system (we use **Ubuntu**) directly inside Windows. It's not a "fake" version; it's a real Linux kernel. This means your code will run exactly the same way on your laptop as it does on the powerful servers that host sites like GitHub, Shopify, and Airbnb.

**Why do we use Linux for Rails?**
Most of the internet runs on Linux servers. By developing in WSL, you are working in an environment that is almost identical to where your app will eventually live. This prevents the "it works on my machine" problem where an app works on Windows but breaks when you try to put it online. Linux also has a much better "package management" system, making it easier to install the complex tools we need.

### 2. Ruby: The Language of Elegance 💎
Ruby is the programming language we'll use. It was created in Japan by Yukihiro "Matz" Matsumoto with a focus on "developer happiness." Matz wanted a language that felt natural to write, almost like English. If our app were a car, Ruby would be the engine.

**What makes Ruby special?**
Ruby is "object-oriented," which means we can model our code after real-world things. In our Island Formulator app, we'll have "objects" for Ingredients, Recipes, and Batches. This makes the code much easier to reason about as the project grows.

### 3. Rails: The Master Blueprint 🏗️
Rails is a "framework" built on top of Ruby. If Ruby is the engine, Rails is the entire car—the wheels, the seats, and the dashboard are already designed for you. It gives us a set of rules and tools so we don't have to build everything from scratch. It's famous for "Convention over Configuration," meaning it makes smart choices for you so you can focus on building your unique features.

**The Rails Philosophy**
Rails follows the "DRY" principle: **Don't Repeat Yourself**. It's designed to help you write as little code as possible to get the job done. It also uses the "MVC" (Model-View-Controller) pattern, which is the industry standard for organizing web applications. You'll learn all about this in the coming weeks!

### 4. PostgreSQL: The Professional Filing Cabinet 🗄️
Every app needs to remember things (like a list of oils, butters, and scents). PostgreSQL (or "Postgres") is our database. It's a world-class, industrial-strength filing cabinet that can hold millions of records and find them in a split second.

**Why Postgres?**
While there are simpler databases, Postgres is the gold standard for professional Rails apps. it supports complex data types and is incredibly reliable. Learning Postgres now will give you a skill that is highly valued in the job market.

### 5. Git & GitHub: The Time Machine & The Hub ⏳
Git tracks every change you make to your code. If you break something, you can "roll back" to a version that worked. GitHub is the online home for your Git projects. It's where you'll store your code, collaborate with others, and show off your portfolio to potential employers.

**The Power of Version Control**
Imagine you're writing a long essay and you want to try a completely different ending without losing your current one. In Git, you can create a "branch," try your new idea, and if it doesn't work, just delete the branch and go back to exactly where you were. It's the ultimate safety net for developers.

---

## 🚀 Quick Verification: Are You Already Set Up?

**You've already completed WSL and GitHub SSH setup in previous training.** Let's verify everything is working before we proceed. This will save you time!

### Run These Verification Commands

Open your **Ubuntu terminal** (search "Ubuntu" in Windows Start menu) and run each command:

1. **Check WSL version:**
   ```bash
   wsl -l -v
   ```
   ✅ **What you need:** Ubuntu listed with VERSION 2

2. **Check Git:**
   ```bash
   git --version
   ```
   ✅ **What you need:** git version 2.x or higher

3. **Check GitHub SSH connection:**
   ```bash
   ssh -T git@github.com
   ```
   ✅ **What you need:** "Hi [your-username]! You've successfully authenticated..."

4. **Check Git configuration:**
   ```bash
   git config --global user.name
   git config --global user.email
   ```
   ✅ **What you need:** Your name and email displayed

### 📊 Verification Results

**ALL 4 checks passed?** 
✅ **Great! You can skip to [Part 4: Install Ruby & Rails](#part-4-install-ruby--rails-in-wsl)**

**ANY check failed?**
❌ Go to the section that matches your issue:
- WSL not version 2? → [Part 1: Verify & Prepare WSL](#part-1-verify--prepare-wsl)
- Git not installed or not configured? → [Part 2: Configure Git in WSL](#part-2-configure-git-in-wsl)
- SSH connection failed? → [Part 3: GitHub SSH Setup](#part-3-github-ssh-setup-critical-)

---

**📝 Note:** Even if you passed all checks, we recommend **quickly reviewing Part 3 (GitHub SSH Setup)** to ensure you understand how SSH keys work. This knowledge is critical for the weeks ahead.

---

## What You'll Achieve

By the end of this tutorial, you will have:
- [ ] **WSL 2 (Ubuntu)**: A real Linux system running inside Windows.
- [ ] **Git Configured**: Your identity set up within the Linux environment.
- [ ] **GitHub SSH Connection**: A secure, password-less link to GitHub (CRITICAL).
- [ ] **Ruby 3.4+**: The language our app is written in (installed via rbenv).
- [ ] **Rails 8.1+**: The framework that makes building web apps fast and fun.
- [ ] **PostgreSQL 14+**: The database where we'll store all our ingredient data.
- [ ] **VS Code with WSL Integration**: Your text editor talking directly to Linux.

---

## Part 1: Verify & Prepare WSL

You should already have WSL installed. Let's make sure it's the right version and working correctly.

### Check WSL Version
1. Open **PowerShell** or **Command Prompt** on Windows (Search for "PowerShell" in the Start menu).
2. Type the following command and press Enter:
   ```powershell
   wsl -l -v
   ```
3. **What you should see**: You should see `Ubuntu` listed with version `2`. 
   - **If it says version 1**: Run `wsl --set-version Ubuntu 2`. This is important because version 2 is much faster for Rails development.
   - **If you don't see Ubuntu**: You might need to install it from the Microsoft Store. Search for "Ubuntu 22.04 LTS".
   - **Troubleshooting**: If you get an error about "Virtualization not enabled," you may need to enter your computer's BIOS settings to enable it. Ask an instructor for help if this happens!

### Opening Your Ubuntu Terminal
From now on, **99% of your work will happen inside the Ubuntu terminal**, NOT the Windows Command Prompt.
1. Click the Start menu and type **Ubuntu**.
2. Open the app. You'll see a black window with a prompt like `yourname@computername:~$`.
3. This is your Linux home. Welcome!

---

## Part 2: Git Configuration in WSL

Even if you have Git on Windows, we need to make sure it's configured inside your Linux (WSL) environment.

### Verify Git Installation
In your **Ubuntu terminal**, type:
```bash
git --version
```
**What you should see**: `git version 2.x.x`. 
- If it says "command not found," run:
  ```bash
  sudo apt update && sudo apt install git -y
  ```

### Configure Your Identity
Git needs to know who is making changes so it can label your "saves" (commits) correctly. Run these commands (replace with your actual name and email):
```bash
git config --global user.name "Your Full Name"
git config --global user.email "your.email@example.com"
```
*Note: Use the same email you used to sign up for GitHub.*

---

## Part 3: GitHub SSH Setup (CRITICAL) 🔑

This is the most important part of your setup. We will create a secure "handshake" between your computer and GitHub.

### Why SSH Keys?
Normally, when you push code to GitHub, it asks for your username and a "Personal Access Token." This is annoying to type every time. **SSH Keys** act like a digital keycard. 
- **Private Key**: Stays on your computer (like your physical house key). **Never share this!**
- **Public Key**: Goes on GitHub (like the lock on your front door).
When you try to connect, GitHub checks if your private key matches the public lock. If it does, you're in! No passwords required.

### Step 1: Generate the Key Pair
In your **Ubuntu terminal**, run:
```bash
ssh-keygen -t ed25519 -C "your.email@example.com"
```
1. **Save Location**: It will ask "Enter file in which to save the key." Just press **Enter** to use the default location.
2. **Passphrase**: It will ask for a passphrase. 
   - For the easiest experience, just press **Enter** twice (no passphrase).
   - For extra security, type a password. Note: You won't see any characters as you type!

### Step 2: Add Your Key to the SSH Agent
The "agent" is a background program that remembers your keys so you don't have to.
```bash
# Start the agent
eval "$(ssh-agent -s)"

# Add your key to the agent
ssh-add ~/.ssh/id_ed25519
```

### Step 3: Add the Public Key to GitHub
Now we need to give GitHub the "lock" part of your key.
1. View your public key by typing:
   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```
2. **Copy the entire output**: Highlight the text starting from `ssh-ed25519` all the way to your email, then right-click to copy.
3. Go to [GitHub.com](https://github.com) and log in.
4. Click your profile photo (top right) -> **Settings**.
5. In the left sidebar, click **SSH and GPG keys**.
6. Click the green **New SSH key** button.
7. **Title**: Give it a name like "My WSL Laptop".
8. **Key type**: Keep as "Authentication Key".
9. **Key**: Paste your key into the box.
10. Click **Add SSH key**.

### Step 4: Test Your Connection
This is the moment of truth. Go back to your **Ubuntu terminal** and type:
```bash
ssh -T git@github.com
```
1. **The Warning**: You will likely see: `The authenticity of host 'github.com' can't be established... Are you sure you want to continue connecting?`
2. **The Answer**: Type **yes** and press Enter.
3. **The Success Message**: You should see: `Hi username! You've successfully authenticated, but GitHub does not provide shell access.`

**If you see your GitHub username in that message, congratulations! You have successfully linked your Linux environment to the cloud.**

---

## Part 4: Install Ruby & Rails in WSL

Now we build the engine of our app. We use a tool called `rbenv` to manage Ruby. This is better than installing Ruby directly because it lets us have different versions for different projects.

### 1. Update System Packages
Linux needs some "building blocks" to be able to install Ruby.
```bash
sudo apt update
sudo apt install -y build-essential libssl-dev libreadline-dev zlib1g-dev libyaml-dev libreadline-dev libncurses5-dev libffi-dev libgdbm-dev
```

### 2. Install rbenv
```bash
# Clone rbenv into your home folder
git clone https://github.com/rbenv/rbenv.git ~/.rbenv

# These lines tell your terminal to load rbenv every time it starts
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc

# Refresh your terminal so it sees the new settings
source ~/.bashrc

# Install the ruby-build plugin (this actually does the installing of Ruby)
mkdir -p "$(rbenv root)"/plugins
git clone https://github.com/rbenv/ruby-build.git "$(rbenv root)"/plugins/ruby-build
```

### 3. Install Ruby 3.4.8
This step takes about 5-10 minutes. Your computer is downloading the Ruby source code and compiling it specifically for your machine.
```bash
rbenv install 3.4.8
rbenv global 3.4.8
```
**Verify**: Type `ruby -v`. It should say `ruby 3.4.8`.

### 4. Install Rails 8.1
Rails is a "Gem" (a Ruby package). We'll also install `bundler`, which manages all the other gems our app will need.
```bash
gem install bundler
gem install rails -v 8.1.2
```
**Verify**: Type `rails -v`. It should say `Rails 8.1.2`.

---

## Part 5: Install PostgreSQL in WSL

Postgres is our database. In WSL, we install it as a service.

1. **Install**:
   ```bash
   sudo apt install -y postgresql postgresql-contrib libpq-dev
   ```
2. **Start the Service**:
   Unlike Windows apps, Linux services don't always start automatically.
   ```bash
   sudo service postgresql start
   ```
3. **Create Your User**:
   By default, Postgres has a "super user" named `postgres`. We want to create a user that matches your Linux username so Rails can talk to it easily.
   ```bash
   sudo -u postgres createuser -s $(whoami)
   ```

---

## Part 6: Install VS Code with WSL Extension

VS Code is your "Workbench." Even though it's a Windows app, it can "remote" into your Linux environment.

1. Download and install **VS Code** on Windows.
2. Open VS Code.
3. Click the **Extensions** icon (the 4 squares on the left).
4. Search for and install the **WSL** extension by Microsoft.
5. **The Magic Connection**:
   - Look at the very bottom-left corner of VS Code. You'll see a small blue icon `><`.
   - Click it and select **Connect to WSL**.
   - VS Code will restart. Look at the bottom-left again; it should now say `WSL: Ubuntu`.
6. **Install Ruby LSP**:
   - While connected to WSL, search for the **Ruby LSP** extension.
   - Click **Install in WSL: Ubuntu**. This gives you features like code highlighting and error checking.

---

## Part 7: Complete Workflow Test 🚀

Let's prove everything works by creating an app, connecting it to a database, and pushing it to your assignment repository.

**IMPORTANT**: We're going to create the Rails app INSIDE your assignment repository (the folder you cloned from GitHub Classroom).

### 1. Navigate to Your Assignment Repository
In your **Ubuntu terminal**, navigate to where you cloned your assignment:
```bash
cd ~/week0-environment-setup-yourusername  # Replace with your actual repo name
```

**Not sure where it is?** Run `pwd` to see your current location. If you don't see your assignment folder, you may need to clone it first using the SSH URL from your GitHub Classroom assignment.

### 2. Create the Test App Inside This Repository
Now create the Rails app as a subdirectory:
```bash
rails new workshop_test --database=postgresql
cd workshop_test
```

### 3. Create the Database
Rails needs to set up the "filing cabinet" for this specific app.
```bash
rails db:create
```
**What you should see**: `Created database 'workshop_test_development'` and `Created database 'workshop_test_test'`.

### 4. See it in the Browser
Start the Rails server:
```bash
bin/rails server
```
1. Open your Windows browser (Chrome, Edge, etc.).
2. Go to `http://localhost:3000`.
3. **The Moment of Truth**: You should see a bright page with the Rails logo saying "Yay! You're on Rails!"

Press **Ctrl+C** to stop the server when you're done celebrating!

### 5. Submit Your Assignment (Push to GitHub)
Now let's submit your work. This proves your SSH connection is working AND completes your assignment.

In your terminal:
```bash
cd ..  # Go back to the assignment repository root
git status  # See what files were created
git add workshop_test  # Add the entire Rails app
git commit -m "Complete Week 0 setup - Rails environment working"
git push origin main
```

**What should happen**: The push should complete WITHOUT asking for a password (because you're using SSH). After a few seconds, you should see "Writing objects: 100%... done!"

### 6. Verify Your Submission
Go to your assignment repository on GitHub (the URL looks like `https://github.com/classname/week0-environment-setup-yourusername`) and you should see the `workshop_test` folder with all the Rails files inside.

**If the push succeeds and you see your code on GitHub, your environment is PERFECT and your assignment is submitted!** 🎉

---

## Common WSL Issues & Troubleshooting

| Issue | Solution |
| :--- | :--- |
| **`sudo service postgresql start` fails** | Try `sudo /etc/init.d/postgresql start`. Sometimes WSL needs the full path to the script. |
| **`rails db:create` says "role does not exist"** | You missed the `createuser` step in Part 5. Run: `sudo -u postgres createuser -s $(whoami)` |
| **`localhost:3000` doesn't load** | Make sure the terminal says "Listening on http://0.0.0.0:3000". If it says "Address already in use," another app is using that port. |
| **SSH "Permission Denied"** | Ensure you added the **Public** key (.pub) to GitHub, not the private one. Run `ssh-add -l` to see if your key is loaded. |
| **`rbenv: command not found`** | You need to refresh your terminal. Run `source ~/.bashrc`. |
| **Windows Firewall Popup** | If Windows asks if you want to allow "Ruby" or "Rails" to access the network, click **Allow**. |


---

## Final Verification Checklist

Before Week 1 starts, make sure you can check all these boxes:

- [ ] I can open the **Ubuntu** terminal.
- [ ] `wsl -l -v` shows Ubuntu is version 2.
- [ ] `ssh -T git@github.com` greets me by my GitHub username.
- [ ] `ruby -v` shows 3.4.8.
- [ ] `rails -v` shows 8.1.2.
- [ ] I can see the "Yay! You're on Rails!" page at `localhost:3000`.
- [ ] I successfully pushed the `workshop_test` app to my assignment repository on GitHub.

**Great job!** You've cleared the hardest hurdle in web development: the setup. You now have a professional-grade development environment. See you in Week 1!
