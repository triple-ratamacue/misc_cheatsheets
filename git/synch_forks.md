>### 1. Clone your forked repo:

    git clone https://github.com/username/yourforkedrepo.git

### 2. Add remote from original repository in your forked repository: 

    cd into/cloned/fork-repo
    git remote add upstream https://github.com/username/repoyouforkedfrom.git
    git fetch upstream

### 3. Updating your fork from original repo to keep up with their changes:

    git pull upstream master
