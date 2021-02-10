# Intro to Git and Github
Before first meeting read introductory material: 
1. [git handbook](https://guides.github.com/introduction/git-handbook/)
2. [source code management](https://www.atlassian.com/git/tutorials/source-code-management)

## First meeting: Intro to git 
### Review intro material, answer questions
### Demo:
#### Section 1: Initialize git
0. Install git
Windows:
- conda install -c anaconda git
- `git config --global user.email "you@example.com:`
- `git configure --global user.name "Your Name"`

1. Make a directory called `git-demo`
   - In the terminal navigate to directory you’re going to create your new folder in
   - `mkdir git-demo`
   - `cd git-demo`
   - Open in IDE: `code .` for VS Code: 
      * Launching from the command line
      * Launch VS Code.
      * Open the Command Palette (⇧⌘P) and type 'shell command' to find the Shell Command: Install 'code' command in PATH command.
      * Restart the terminal for the new $PATH value to take effect. You'll be able to type 'code .' in any folder to start editing files in that folder.
2. Initialize git for this directory
   -  In terminal `~git-demo$ git init`
    *This will create a .git folder that has all the data in it to track changes.*  

3. Create new file called index.py (or index.js) and add content
    - `~git-demo$ touch index.py`
    - In `index.py` add 
    ```Python 
    print(“Hello world”)
    ```
4. Commit changes
    - Get git status (optional but helpful)
      - Terminal: `~git-demo$ git status`
        *This will tell you the current status of your directory. Right now it should tell you that you have no commits and you have one untracked file.*
      - VS Code GUI: click source control button on the left hand side of the editor
			*This is a more visual representation of your current changes. Red shows delete content and green shows new content.*

    - Add changes
    	- Command line: `~git-demo$ git add .`
    	- VS Code GUI:  In the version control view, click the + button next to your new file to “stage” your changes

    - Make a commit message:
    	- Command line: `~git-demo$ git commit -m “adding new file”
    	- VS Code GUI: In the text field type your message and click the checkbox

#### Section 2: Branching and merging
1. Create a branch. <br />
	*Branches can help keep a chunk of work separate from your main working code. You can use them to try a new version of a package while knowing your main branch still works, make a new feature, etc.*
    - Terminal:` ~git-demo$ git checkout -b feature/adding-argv`.<br />
		*This says, “create a new branch (-b) named “feature/adding-argv” and take me there (checkout). We use `feature/` and `bugFix/` prefixes to branch names to let other people know what type of work is being done on this branch.*

2. Add changes: 
    - Change your `index.py` to be 
```Python
import sys
print('Hello there', sys.argv[1])
```

3. Commit changes to the branch (follow step 4 in section 1). 
4. Checkout master branch
    - Terminal:` ~git-demo$ git checkout master`.<br />
*This says “take me to the ref named “master””, in this case a branch. We don’t need the -b anymore because master already exists as a branch.*
    - Look at your file, it no longer has the changes we just saved to the adding-argv branch. 
5. Rename master branch to main
    - Terminal:  `~git-demo$ git branch -m master main`
    - VS Code: In source control, click the three little dots to get a drop down menu, go to <strong>Branch… > Rename branch</strong>
6. Merge your changes into your main branch
    - Terminal: :` ~git-demo$ git merge feature/adding-argv`.
    - VS Code: In source control, click the three little dots to get a drop down menu, go to Branch… > Merge branch, select the branch you want to merge. 
