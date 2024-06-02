### Task 1: Setup a Remote Repository in Local, Add a File and Commit, Save the Changes, and Push to Master Branch

**Solution:**

1. **Configure Git**  
First, we need to configure Git with our name and email.

    ```bash
    git config --global user.name "our Name"
    git config --global user.email "our_email@example.com"
    ```

2. **Make a Directory**  
Create a new directory for our project and navigate into it.

    ```bash
    mkdir my-project
    cd my-project
    ```

3. **Clone the Remote Repository in Local**  
Clone the remote repository to our local machine. This step assumes the remote repository already exists. If not, create it first on GitHub or another Git hosting service.

    ```bash
    git clone https://github.com/username/our-repo-name.git
    cd our-repo-name
    ```

4. **Initialize a Local Repository**  
If we didn't clone a repository (i.e., starting from scratch), we need to initialize a local repository. If we cloned the repository in the previous step, we can skip this.

    ```bash
    git init
    ```

5. **Add a Remote Repository**  
Link our local repository to the remote repository. Again, skip this if we cloned the repository.

    ```bash
    git remote add origin https://github.com/username/our-repo-name.git
    ```

6. **Create a File and Add Content**  
Create a new file and add some initial content to it.

    ```bash
    echo "Hello, World!" > hello.txt
    ```

7. **Add the File to Staging Area**  
Stage the new file so that it can be committed.

    ```bash
    git add hello.txt
    ```

8. **Commit the Changes**  
Commit the staged file to our local repository with a message.

    ```bash
    git commit -m "Add hello.txt with initial content"
    ```

9. **Push to the Master Branch**  
Push our changes to the master branch of the remote repository. Note that GitHub has moved to using `main` as the default branch name, but if our remote repository uses `master`, use `master` instead.

    ```bash
    git push -u origin main
    ```

    If our default branch is `master`, replace `main` with `master`:

    ```bash
    git push -u origin master
    ```

### Task 2: Create a New Branch, Commit and Push the Changes to New Branch, and Merge it with the Master Branch Using Pull Request

**Solution:**

1. **Create a New Branch**  
We need to create a new branch from the master branch. This new branch will be used to add our new feature.

    ```bash
    git checkout -b new-feature-branch
    ```

    This command creates a new branch named `new-feature-branch` and switches to it.

2. **Make Changes and Add to Staging Area**  
Make the necessary changes for the new feature. For demonstration, we'll create a new file named `feature.txt` and add some content to it.

    ```bash
    echo "New feature" > feature.txt
    git add feature.txt
    ```

    - `echo "New feature" > feature.txt`: This command creates a file named `feature.txt` with the content "New feature".
    - `git add feature.txt`: This command adds the `feature.txt` file to the staging area.

3. **Commit the Changes**  
Commit the changes made to the new branch with a descriptive message.

    ```bash
    git commit -m "Add new feature"
    ```

    - `git commit -m "Add new feature"`: This command commits the changes in the staging area with the message "Add new feature".

4. **Push the New Branch to Remote**  
Push the newly created branch to the remote repository.

    ```bash
    git push -u origin new-feature-branch
    ```

    - `git push -u origin new-feature-branch`: This command pushes the `new-feature-branch` to the remote repository and sets the upstream branch.

5. **Create a Pull Request**  
Go to our repository on GitHub and create a pull request to merge the `new-feature-branch` into the `main` (or `master`) branch.

    - Go to the GitHub repository where our project is hosted.
    - We should see a notification about the recently pushed branch. Click on the "Compare & pull request" button.
    - Review the changes that we made in the `new-feature-branch`.
    - Provide a title and description for the pull request if necessary.
    - Click the "Create pull request" button.

6. **Merge the Pull Request**  
Once the pull request is created, it needs to be reviewed and then merged into the `main` (or `master`) branch.

    - After the pull request is reviewed and approved, click on the "Merge pull request" button.
    - Confirm the merge by clicking the "Confirm merge" button.
    - We can now delete the `new-feature-branch` as it has been successfully merged into the `main` (or `master`) branch.

### Task 4: Resolve Merge Conflicts

**Solution:**

1. **Attempt to Merge Branches**  
First, we attempt to merge the branches. We need to switch to the `master` branch and merge the `new-feature-branch` into it.

    ```bash
    git checkout master
    git merge new-feature-branch
    ```

    - `git checkout master`: This command switches to the `master` branch.
    - `git merge new-feature-branch`: This command attempts to merge the `new-feature-branch` into the `master` branch.

2. **Identify the Conflicted Files**  
Git will output which files have conflicts. We need to take note of these files.

3. **Open the Conflicted Files and Manually Resolve Conflicts**  
Open each conflicted file in a text editor. Look for conflict markers like `<<<<<<<`, `=======`, and `>>>>>>>`. Manually resolve the conflicts by editing the file and removing the conflict markers.

    Conflict markers look like this:

    ```text
    <<<<<<< HEAD
    This is content from the master branch.
    =======
    This is content from the new-feature-branch.
    >>>>>>> new-feature-branch
    ```

    We need to choose which changes to keep or combine the changes as needed, then remove the conflict markers.

4. **Add the Resolved Files to Staging Area**  
After resolving the conflicts, we add the resolved files to the staging area.

    ```bash
    git add resolved-file.txt
    ```

    - `git add resolved-file.txt`: This command stages the resolved file.

5. **Commit the Resolved Changes**  
We then commit the resolved changes.

    ```bash
    git commit -m "Resolve merge conflicts"
    ```

    - `git commit -m "Resolve merge conflicts"`: This command commits the resolved changes with a message.

6. **Continue the Merge Process**  
Finally, we continue the merge process.

    ```bash
    git merge --continue
    ```

    - `git merge --continue`: This command tells Git to continue the merge process after resolving conflicts.

By following these steps, we can effectively resolve merge conflicts and complete the merge process.

### Task 5: Practice More Git Commands

**Solution:**

1. **Check the Status of Our Repository**  
To see the current status of our repository, including changes that are staged, unstaged, and untracked, use:

    ```bash
    git status
    ```

2. **View the Commit History**  
To view the commit history of our repository, use:

    ```bash
    git log
    ```

3. **Create and Switch to a New Branch**  
To create a new branch and switch to it immediately, use:

    ```bash
    git checkout -b another-branch
    ```

    - `git checkout -b another-branch`: This command creates a new branch named `another-branch` and switches to it.

4. **Merge a Branch into the Current Branch**  
To merge changes from another branch into the current branch, use:

    ```bash
    git merge branch-to-merge
    ```

    - `git merge branch-to-merge`: This command merges the specified `branch-to-merge` into the current branch.

5. **Stash Changes**  
To temporarily save changes that are not yet ready to be committed, use:

    ```bash
    git stash
    ```

    - `git stash`: This command stashes our current changes, allowing us to work on a clean working directory.

6. **Apply Stashed Changes**  
To apply the stashed changes back to our working directory, use:

    ```bash
    git stash apply
    ```

    - `git stash apply`: This command applies the most recently stashed changes back to our working directory.

7. **List All Branches**  
To list all branches in our repository, use:

    ```bash
    git branch
    ```

    - `git branch`: This command lists all local branches in our repository.

8. **Delete a Local Branch**  
To delete a local branch that is no longer needed, use:

    ```bash
    git branch -d branch-to-delete
    ```

    - `git branch -d branch-to-delete`: This command deletes the specified `branch-to-delete`.

9. **Fetch Updates from Remote Repository**  
To fetch updates from the remote repository without merging them, use:

    ```bash
    git fetch
    ```

    - `git fetch`: This command downloads updates from the remote repository but does not merge them into our local branch.

10. **Rebase Our Branch**  
To rebase our current branch onto the latest commit of the `master` branch, use:

    ```bash
    git rebase master
    ```

    - `git rebase master`: This command rebases our current branch onto the `master` branch, applying our commits on top of the latest commits from `master`.

By practicing these commands, we can become more proficient in using Git for version control.

