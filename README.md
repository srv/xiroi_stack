dis# Xiroi stack

## Installation

Clone this repository and execute the script `install_first_time.sh`

    (xiroi_stack)$ ./install_first_time.sh

Wait for the code to download.

## Working with submodules
### Pull & push twice

 1. Pull twice: On the main repository execute `git pull && git submodule foreach git pull`.
 2. Push twice: Work with the code in any submodule as usual. Commit and push as usual. At the end, go to the main repository and check what a `git status` shows. It will normally show that a particular repo has changed. For example:

 Say we have a main repo called *robot* and a submodule called *sensor*. If we update it, we have to commit twice, one for the submodule and another for the main repo.

      $ ls robot/
           ./
           ../
           sensor/
      $ cd sensor
      $ git touch test.txt
      $ git add test.txt
      $ git commit -m "added file test"
      $ git push
      $ cd ..
      $ git status
          On branch master
          Your branch is up-to-date with 'origin/master'.

          Changes not staged for commit:
            (use "git add <file>..." to update what will be committed)
            (use "git checkout -- <file>..." to discard changes in working directory)
            (commit or discard the untracked or modified content in submodules)

            modified:   sensor (modified content)

          no changes added to commit (use "git add" and/or "git commit -a")
      $ git add sensor
      $ git commit -m "updated sensor reference"
      $ git push

### Remove submodule
To remove a submodule you need to:

- Delete the relevant section from the .gitmodules file.
- Stage the .gitmodules changes git add .gitmodules
- Delete the relevant section from .git/config.
- Run git rm --cached path_to_submodule (no trailing slash).
- Run rm -rf .git/modules/path_to_submodule (no trailing slash).
- Commit git commit -m "Removed submodule <name>"
- Delete the now untracked submodule files rm -rf path_to_submodule

