# Service Now Git Demo - Huntington

## This is a simple guide and introduction to using github on your huntington laptop

### Step 1 - Installation and Start up

1. Open Software Center. Download and install `Git for Windows`, `Visual Studio Code`
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

> You can run ```git remote -v``` to check if your origin is set correctly.

2. We are ready to push our code up to the remote: ```git push origin master```. Master incidates the branch we are pushing to.
3. Got back to Github and refresh. You should see your changes.
5. Hit the pencil edit button on the READ.md file.
6. Add this line: ```## This is short demo for pull purposes.```
7. Add a commit message
8. Commit change. This is the same process we just applied, but we are using a GUI rather than a Command prompt.

#### Pull

It is **important** to note that anytime you are working in colaboration on a repository and you are sharing the same branch, you must pull the latest code down before you start working. This avoids future conclicts in the repository.

1. Return the command prompt and run: ```git fetch```
2. After it downloads any changes, run: ```git pull```
3. You are now running on the latest version of the code inside the master branch

#### Branching

At any time during development, Git allows you to branch off code. This helps when you would like to update a feature on a specific version and can also help avoid future conflicts by working on a personal branch.

1. To create a new branch: ```git branch dev```. This creates a new branch name dev
2. To list all available branches: ```git branch```
3. To switch and checkout to a new branch ```git checkout dev```
4. Creating a branch doesn't push it up to your origin. You must call a command to do that: ```git push origin dev```


### Step 4 - VS Code Intro

For those not familar with VS Code, this is a light weight editior built by Microsoft which many devs have gravitated towards. Great search capability, built in source control, and ability to add exentions.

1. Open Visual Studio Code
2. Hit Open Folder, and use the same folder we've created for this demo.
 > You'll see an explorer on your left with 5 main tab iconns. Explorer, Search, Source Control, Debugging, and Exentions. Notice you can see the ReadMe.md file we created in your explorer.
 
 Let's quickly create a file, commit, and push it through VS code.

 3. Create the a folder named "Scripts" using explorer.
 4. Create a script file named. glideRecord.js
 5. Copy the following code block into your new file: 
 ```
 var user = new GlideRecord('sys_user');
user.addQuery('sys_id', "Some sys ID");
user.query();
while(user.next()){
    gs.log(user.email);
}
 ```

 6. Save the file.
 7. Before we commit, lets use the **dev** branch we crated during our branch section.
 8. Use the tree log on the bottom right of VS code. It should say master. We clicked, a menu will apear from the top. You'll see a list of available branches. Select dev.
 9. We are ready commit. Select the source control from the left nav. Type a commit message in the top right text box, then hit the check box. If a prompt appears about staging files, click "always"
 10. Our code is commited and all that is left to do is to push our code. Towards the bottom left, you'll see our branch name and a `0` down, and `1` up. The means there are no changes to pull down, and one commit change to push up. Click the sync button and our code will be pushed up.
 
 #### Stashing

Stashing is a great way to save code without commiting and pushing. We can see a use case of stashing by saving the code to the incorrect branch.

1. Change the branch to `master`
2. Add a new script file named ```dev.js``` and use the following code:

```
//Test file for dev branch

let env = "dev";

```

3. Save the file.

We've saved the file to the wrong branch so now we must use stash

3. First track the new file: ```git add .```
4. Run: `git stash`. You'll notice in VS code, the change ready to commit is now gone.
5. Change your branch back to dev. Confrim with git status.
6. Run: ```git stash apply```. The change comes back in your source control view in VS code.
7. Commit your changes to the correct branch.

 #### Merging

 To merge our new dev branch in master, lets go back to our repo on github.com. You'll see that have a recent push to our dev branch. There will be a green button "Compare and pull request". Since we are mergeing `dev` into `master`, make sure the base is master, and we comparing dev.

 1. Create the pull reqeust with the correct base, and compare.
 2. You can review all the changes, diffs, and commits before you merge.
 3. Merge pull request and confirm
 4. Our home page for the repo will reflect all the changes we made in the master branch

### Step 5 - Git integration in ServiceNow

#### Linking Github account

1. Create a new project in Github, and copy the clone link
2. Create New Applicaton named `My New SN App`
3. Open Studio
4. Select the "Link Source Control" from the "Source Control" Menu
5. Enter the new repo link, and login.

#### Importing from Source Contrl

1. Fork this repo `https://github.com/ServiceNow/devtraining-needit-madrid.git`
2. Using the fork, you know have created your own copy on your github account with the repo.
3. Enter the clone link and your account details
4. Application is loaded into your instance

#### Using Branches

1. You can switch branches from any number of branches that have been created
2. Create a tag before creating a new branch.
3. When creating a new branch, select your new tag.

#### Commiting Code

1. Make any change. 
2. By using the "Apply Remote Changes" menu, you can push any changes
3. Review your changes, and apply the changes.
4. This only stashes the changes, and does not push them to the remote repo.
5. There is a "Manage Stashes" menu. From here, you can review and stashes, and then apply.
6. Use the "Commit Messages" menu, give it a message, and commit the new code
7. 


In summary, we have learned how to create a github repo, push & pull code, branch & and merge through the command line. We then follow the same procedure in VS Code and ServiceNow GUI's

For any questions: agustin.ortiz@huntington.com





