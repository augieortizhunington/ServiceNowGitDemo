# Service Now Git Demo - Huntington

## This is a simple guide and introduction to using github on your huntington laptop

### Step 1 - Installation and Start up

1. Open Software Center. Download and install `Git for Windows`, `Visual Studioi Code`
2. Once complete, you should see a Git folder in your Program files. Searching in windows, you should find **Git Bash**, **Git CMD**, and **Git GUI**
3. **Open Git Bash**

> Note this a Unix/Linux shell and will not accpet Windows Commands. Linux cheatsheet can be found [here](http://cheatsheetworld.com/programming/unix-linux-cheat-sheet/).

4. Inside of your shell, you will be in root PC folder `U:\`. 
5. Run the command: ```git```. You should see a list of help commands. This confirms you have git installed and ready to use.

> You are likely to run into a few issues while intializing your first repo.

### Step 2 - Create Git Hub Account & Repository

1. Go to [Github.com](https://github.com), and create an account if you don't have one.
2. After login, create a new repo. 
3. Name it `SeviceNowHuntingtonDemo` and hit Create repository

You now have an empty repository. We will start using git commands in the next step.

### Step 3 - Git Into

Here is a pdf [cheat sheet](https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf)

#### Clone 

1. Copy the https link on the home page of repo on github. Should look like `https://github.com/augieortizhunington/ServiceNowHuntingtonDemo.git`

> You are likely to run into a few issues while intializing your first repo. If you run into issues, make sure you are in the root directory `U:\`. If you see SSL errors, update your configs by running: ```git config --global http.sslVerify false```

2. Go back in your shell
3. Run command: ```git clone https://github.com/augieortizhunington/ServiceNowHuntingtonDemo.git``` (Replace with your link). This just created a copy of the repository on your local machine.
4. Run: ```cd ServiceNowHuntingtonDemo```. This will change your directory into the new local repo.
5. You are know ready to contribue to the repo.

#### Add Files

1. Let's start by adding a simple ReadMe file.
2. Run: ```echo "# Service Now Git Demo" >> README.md```. This will simply create an md file within the repo.
3. Run: ```ls```. You should see our new file listed
4. Run: ```git status```. You will see have one untracked file that needs added.
5. Run: ```git add .```. This will add all new files, and stage them.
6. If you run: ```git status``` again, the file is now tracked.

#### Commit

Whenever you have finished a feature or you are at a good stopping place with your code, you should commit the code to the repo. This gives you an idea of what you did, and acts a saving point in your source control.

1. Run: ```git commit -m "Read Me file created"```. The  `-m` is the message being assigned to this commit. 
2. Git status will tell you that your tree is clean and there is nothing left to commit.

#### Push

We have committed our code, and we are ready to push it to the remote repoostiroy. Remote meaning that the code is ready to back up to your source control. We are ready to send our changes up to Github.

1. Set your remote origin by running: ```git remote add origin https://github.com/augieortizhunington/ServiceNowHuntingtonDemo.git```. It's possible it's already added since we've cloned the repo.
2. We are ready to push our code up to the remote: ```git push origin master```. Master incidates the branch we are pushing to.
3. Got back to Github and refresh. You should see your changes.

#### Pull









