This is a repository for demonstrating Gitflow branching model using Gitflow Extension.

Credits and thanks to Vincent Driessen for proposing a robust Gitflow model and also providing an extension, which helps in simplifying workflow for a robust enterprise release management.

Below process is based on Gitflow model proposed by him http://nvie.com/posts/a-successful-git-branching-model/

Installing a Gitflow Extension

Installation instructions can be found for different platforms here. However, we will provide a simplified step to get it up and running on windows.

Download and install Git for Windows. By default, it would install in this directory “C:\Program Files\Git”.
Next you need to get these three files getopt.exe from util-linux package , libintl3.dll, and libiconv2.dll from the dependencies packages (libintl and libiconv). We have gathered and uploaded all these files for ease of installation, so you could get those from here alternatively.
Once you get those three files copy and paste those files at a location where Git was installed (i.e.,) inside a bin folder at “C:\Program Files\Git\bin”
Next step is to clone or download this repository https://github.com/nvie/gitflow
Once done there will be a folder named “contrib” navigate to that folder (gitflow-develop\contrib).
Open command prompt in that directory in administration mode and type this command msysgit-install.cmd "C:\Program Files\Git"
Git flow will be installed and you could test it by typing Git flow help in command prompt. That’s it Git flow extension is installed & configured in your system ready for use.
Commands related to different branches in a Gitflow model

develop and master branch

Checkout master branch. git checkout master git push -u origin master

Push new branch to remote repository git checkout develop git push origin develop

feature branch

Clone a repository

git clone https://github.com/bharatdwarkani/gitflow-example 
cd gitflow-example 
git checkout develop 
git flow init

Start a feature branch, name of feature branch will be name of feature; here we are using it as feature1 for an example

git flow feature start feature1

Once done. Status of changes can be checked and newly added or modified files.

git status 
git add .
git commit -am "Your message"

Following command will publish feature on to remote repository.

git flow publish feature1 
git push

git flow feature track feature1 instead of git flow feature start feature1 can be used when a feature branch is checkout in different machines

Once a feature is completed and codes are reviewed, developer can complete his work in a branch by issuing following command. On execution, codes will be merged to development automatically and feature branch will be deleted from remote.

git flow finish feature1

If you need to delete a branch you can execute 
git branch -d feature/feature1

release branch

Start a release branch. 
git checkout develop 
git pull 
git flow release start release1

Commit newly added or modified changes and push to remote 
git add . 
git commit -am "Your message" 
git flow publish release1 
git push

Merge changes to develop branch 
git checkout develop
git merge release/release1

After release merge changes of branch to master 
git checkout release/release1 
git pull 
git flow release finish release1 (or)
git flow release finish -m "Your message" "release1"
git checkout master git push --all origin

hotfix branch

Start a new hotfix branch and commit changes after modifications.
git checkout develop 
git flow hotfix start hotfix1
git status 
git add . 
git commit -am "Your message"

Publish branch to remote git flow publish hotfix1

Merge changes to remote 
git flow hotfix finish hotfix1 (or)
git flow hotfix finish -m "Your message" "hotfix1" 
git status 
git checkout master
git push --all origin
