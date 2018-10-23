## Command line instructions

```
Git global setup
git config --global user.name "YourUserName"
git config --global user.email "name@email.com"

//to set the username
git config user.email "email@example.com" 

//to get the username
git config user.email  //will give you the user name associated currently

//to reenter new username and password while doing push or pull
git config --global --unset user.password

//or

If you are MAC user then you can open KeyChain Access Application from finder and 
then look for your account listed there. 
Just click on it and update your password. Now give a try and things will fall in place.

//or

In Windows 10 with Git
Remove/update related Credentials stored in Windows Credentials -
>>Control Panel\All Control Panel Items\Credential Manager
```


```
git clone --recurse-submodules <path of remote repo.git>
git checkout <name of branch>
Git status to know if anything changes locally or which branch you are on
To undo any local changes - git checkout [filenamewithpath]
Git pull 
```

```
List all branches
git branch -a 

//to create a branch - 
got branch <branchName>

//to switch to another branch
git checkout <AnotherBranchName>
```

```
to clone a single branch
git clone --single-branch -b <branchName> host:/dir.git

//to know which git repo is associated currently
git remote -v

Ignore files and folders to push to remote repo
.gitignore

//create a file -
touch .gitignore

mention files and folders that you do not want to push to remote repo

----.gitignore------
log.txt
/folder
```

```
git init
git add.
git status
git commit -m "message"
git remote add origin <remote git path.git>
git remote -v
git config --global --unset user.password
git push -u origin master
Note - above will ask you username and password as we have unset the credentials
```

```
Create a new repository
git clone servername.git
cd mobile-e2e
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master
```

```
Existing folder
cd existing_folder
git init
git remote add origin servername.git
git add .
git commit -m "Initial commit"
git push -u origin master
```

```
Existing Git repository
cd existing_repo
git remote add origin servername.git
git push -u origin --all
git push -u origin --tags
```
