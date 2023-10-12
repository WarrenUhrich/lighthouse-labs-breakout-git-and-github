# Lighthouse Labs | Git and GitHub for Teams

[GitHub Repository Branch](https://github.com/WarrenUhrich/lighthouse-labs-git-and-github-breakout/tree/2023.10.11-web-flex-all-12june2023) | [Vimeo Video Recording](https://vimeo.com/873565071/453756c6f0?share=copy)

* [X] Review GitHub Basics
* [X] Review Git Basics
* [X] Branching in a Repository
* [X] Pull Requests

## GitHub Basics

When it comes to creating a new repository, it is important to note there are two main approaches.

### 1. Create the repository on GitHub first.

1. Navigate to the ["Create a new repository" form on GitHub.com](https://github.com/new).
2. Choose the owner.
3. Add a repository name (ensure it is unique to the owner's other repositories.)
4. Add a description (optional, but best practice.)
5. Add a README (optional, but best practice.)
6. Add a `.gitignore` appropriate for your project (optional, but best practice.)
7. If you are making the repository public, consider [researching licences](https://choosealicense.com/) to ensure it is clear if, or how, others may use your code (optional, but best practice.)

Once your repository is created, clone it to your machine. Click the green "Code" button and copy the clone URL.

```bash
# Navigate to YOUR projects directory
cd ~/lighthouse-labs

# The clone command will create a project directory named after your repo
git clone YOUR_REPO_URL

# Navigate inside of your project directory
cd YOUR_PROJECT_NAME

# Open the project in Visual Studio Code
code .
```

As you make changes, ensure you are frequently adding and commiting your changes. Push to the appropriate branch with each commit to ensure your work is backed-up online.

### 2. Create the repository on your machine first.

If you begin work on your computer *prior* to creating a repository online, there are a few things to watch out for. Let's suppose we're creating an application in our projects directory like so:

```bash
# Navigate to YOUR projects directory
cd ~/lighthouse-labs

# Create a directory for your project
mkdir YOUR_PROJECT_NAME

# Enter the directory
cd YOUR_PROJECT_NAME

# Initialize a local repository here
git init

# In modern projects, it is best practice to name our primary branch: "main"
git branch -m master main # Renames current branch from "master" to "main"

# You can confirm git is active in this server by checking for a hidden .git directory
ls -a # Look for ".git" in the results

# It is best practice to create a README in your project
touch README.md

# It is best practice to create a .gitignore in your project
touch .gitignore

# We have added files, we'll need to stage these changes before we can commit them
git add README.md && git add .gitignore

# Create your first commit
git commit -m "Initial commit; add README and gitignore files"
```

*Need some help setting up your .gitignore file? Consider using [gitignore.io](https://www.toptal.com/developers/gitignore) to get started!*


Next, we need to create a repository on GitHub.com, so that we can push our commits somewhere.

1. Navigate to the ["Create a new repository" form on GitHub.com](https://github.com/new).
2. Choose the owner.
3. Add a repository name (ensure it is unique to the owner's other repositories.)
4. Add a description (optional, but best practice.)
5. Do ***NOT*** add a README (this creates a commit, which will create a history divergent from your local repository!)
6. Do ***NOT*** add a `.gitignore` (this creates a commit, which will create a history divergent from your local repository!)
7. Do ***NOT*** add a licence via this tool (this creates a commit, which will create a history divergent from your local repository!) If you are making the repository public, consider [researching licences](https://choosealicense.com/) to ensure it is clear if, or how, others may use your code (optional, but best practice.) You will want to manually add the licence file and information to your project in a commit later.

Once the GitHub.com repository is created, click the green "Code" button and copy the clone URL. This URL is important for our next step.

Because we already have our project locally, we won't be using the `git clone` command. Instead, we want to update our local repository with information about this `remote` location. Our git repositories can keep track of one or more "remotes," which can be thought of as key-value pairs. ***Each remote name represents an external repository URL***.

```bash
# We can add a new remote key-value pair using the `git remote add` command
# What is happening in this line, is we're telling git that origin=YOUR_REPO_URL
git remote add origin YOUR_REPO_URL

# Now we can push changes to this remote URL
# Instead of having to paste the URL every time, we can use this shorter "remote" name
git push -u origin main # Remember, origin=YOUR_REPO_URL, this just saves us typing!
```

*Note that `-u` is the "upstream branch" flag. It sets the specified branch (`main` in the above) to the default `git pull` and `git push` branch.*

## Git Basics

Once your project is up-and-running as well as connected to your online repository, it is time to get into the git groove!

If you are working in a team, and on a particular feature, ensure you have selected (or created) an appropriate branch.

***Pro tip:*** *Create a branch per-task. Each task should be "bit-sized" for best results. Aim for 1-6 hours per-task, something do-able within a day.*

```bash
# (Ensure you are first in your project directory)

# Switch to current task/feature branch
git checkout -b feature/hello-function

# Make changes for your feature
touch hello.js
echo "module.exports = {hello: name => console.log('Hello, '+name+'!')}" >> hello.js

# Confirm your file is populated with code
cat hello.js

# If you're curious which branch you're on, you can run "git branch" at any time
git branch # Your active branch will be marked with an asterisk "*"

# Great! If we're happy with this addition, let's add it to the stage
git add hello.js

# If you're curious to see which files are on-stage, which aren't, and if there are any other concerns at-present—check using "git status"
git status

# Staged changes can be commited (they will be commited to the active branch)
git commit -m "Add hello function"

# When you commit a new change, it is a good idea to push right away
git push -u origin feature/hello-function
```

The core steps that should be taken away from the above are as follows:

1. `git status`
2. `git add YOUR/FILE.EXTENSION`
3. `git commit -m "YOUR COMMIT MESSAGE"`
4. `git push origin YOUR_BRANCH_NAME`

For commits to gain utility, help more in debugging, and be more digestible to both yourself and your team, please practice writing ⚛ "atomic commits." This is the idea that each commit should be a very small, focused, and descriptive change.

Recall you can have a look at previous commits via: `git log`

## Branching in a Repository

When is the best time to split into a new branch? When is it a good time to commit, or even merge, into the `main` branch?

These are fantastic questions, and the answers may vary a little depending on what your group, team, or company agrees on. We'll go over some rules-of-thumb that may offer you some insight into a particular approach or two that may be effective your projects present and future.

### When should I create a branch?

Even if you're working alone, it can help you stay organized and focused if you create tasks for yourself. Each task should, if possible, be something you estimate might take you anywhere from 1-6 hours (try and keep it lower rather than higher, if possible.)

In order to accomplish this, it is important you take the time either on your own, or as a team, to break down your project and its goals into tiny, bite-sized pieces. Most any problem can be broken down into such pieces, and from these we can create our tasks.

It is easier to define, focus on, and complete ***small clear*** tasks (opposed to large vague ones.) They may require more work to define, but that clarity will save you from wandering off-topic while developing the feature.

For example, let's suppose we're working on a to-do list. ***Avoid*** a task like this:

* [ ] Create to-do app

This is too large and vague. Break down the problem. What steps would you need to take in order to accomplish this?

* [ ] 1. Create repo with `README.md` and `.gitignore`
* [ ] 2. Create base directories and files for project
    * `/public/.gitkeep`
    * `/public/css/.gitkeep`
    * `/public/js/.gitkeep`
    * `/routes/.gitkeep`
    * `/express-server.js`
* [ ] 3. Create database for project
    * This will go in `express-server.js` for this simple example
    * Just a variable for this example: `const todos = [];`
    * (In a real project, create a `/db` directory with `/schema`, `/seeds`, `/queries`, etc.)
* [ ] 4. Add ToDos **Index** route: `GET /todos`
    * Create the `router.get()` for this
    * Add logic and `templateVars`
* [ ] 5. Add Todos **Index** template: `/views/todos/index.ejs`
* [ ] 6. Add ToDos **Create** form route: `GET /todos/new`
    * `<form>` should be `POST`
    * `<input>` must be text and named `task`
* [ ] 7. Add Todos **Create** form template: `/views/todos/create.ejs`
* [ ] 8. Add ToDos **Save** route: `POST /todos`
    * Save new todo item to `todos` array
    * Redirect to `GET /todos` index page
* [ ] 9. Add ToDos **Complete** route: `POST /todos/:id/complete`
    * Remove the target "todo" from the `todos` array
    * Update the `/views/todos/index.ejs` template to have a "complete" button

Something like the above is much better and much clearer. Great time and care should take place in planning our approach from the start. In an ideal project, you already would have planned things like the User Stories, Database Nouns, ERD, Routes, and Wireframes. This would be the steps involved with bringing your project to a development phase, and it is (again) worth the time to break down your tasks. Tools like Trello can be great for communicating this sort of a task list.

## Pull Requests

What is a pull request? And, an important distinction we should make here: is a pull request a feature of `git` or GitHub!?

### What is a Pull Request?

This is a way for us to protect the `main` or `prod`(uction) branch. Why does a branch like `main` need "protecting?"

In real projects, we'll often eventually launch it—but this is not usually the end of its journey. Sooner or later we'll need to either debug something and prepare a fix, or add a new feature. When we're tasked with something like that it is incredibly important that we keep track of the "live" version of the website. This way, should the website go down or something happens, we'll know which version to put back up on the web. This launch-ready or live version of the code is usually represented by the `main` branch.

Even if we're at an earlier stage in development, the `main` branch will at *least* represent the almagamation of all ***completed*** features. That is, to say, that only completed features should ever be placed in this branch. We can see how the weight of this practice becomes very apparent post-launch of a web application.

A "Pull Request" acts as a gateway for commits to be added to the `main` or `prod`(uction) branch. More precisely, it is a way to create a formal request, specifying that you are hoping a particular feature branch will be `pull`ed into the `main` branch. This request is not carried out until a member of the project approves it. In most real projects, as a "check and balance," typically someone other than the person who worked on the feature will review the request. They have the opportunity to make comments, or even reject the request.

Notice that this gives ample opportunity for involved parties to consider the feature, the implementation, and overall approach taken to reach the goal. Back-and-forth regarding the code can take place while the request is open so that improvements or changes can be made to better serve the project. It is also a learning opportunity for involved parties, maybe one of the developers knows a trick or a cleaner way to organize something. Perhaps they know of a method or function that will perform better. Or, perhaps there is a security concern that the first pair of eyes didn't quite catch! In any case, it is a practice that is intended to improve the quality of our code and ensure everyone is on the same page.

### Is a "Pull Request" a git feature, or a GitHub feature?

A quick reminder that...
* `git` is the program we install on our computer to version control our projects.
* `GitHub.com` is a web application that helps us store and organize our repositories in an external site.

When we run commands like...
* `git status`
* `git add -A`
* `git commit -m "Initial commit"`
* `git push -u origin main`

...we should note that all of the above are features of the `git` program.

`GitHub.com`, as a web application, is a website we can visit and engage with our repositories (as well as the repositories of other developers both across the street or across the globe!) We'll find that one of the features of this website is to create a "Pull Request."

The pull request system in GitHub.com will make note of the GitHub.com users, and allows robust community features like providing a title and description for your request—but even more important is the ability to comment on the code in the request. This is where collaboration and learning can happen within the GitHub space.

If everything looks good, you can click "Merge pull request." Effectively, the GitHub.com web application will run the appropriate `git` commands on its server to merge the target branch *into* the `main` branch. Once this is completed, all commits from the feature branch will be present in the `main` branch.

***Important:*** *Once a pull request is approved and merged, all members of the team will want to `pull` the latest changes into their local project directory. This can be accomplished via the following steps:*

```bash
# Make sure you're in your project directory

# Switch to the main branch
git checkout main

# Pull the latest changes into your main branch
git pull origin main

# Switch back to your feature branch
git checkout feature/hello-function

# It is a good idea to keep your branch up-to-date and compatible with the main branch. Consider pulling the changes there as well.
git pull origin main

# After this, run your application again and confirm that it is working properly with these updates.
```
