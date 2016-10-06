# Messing with Git

Typically with a git repository has a master branch and a single remote called origin for master. It is possible to add more than one remote in the same repository. The benefit is that local branches can be pushed to the alternate remote to create a remote copy of the local changes without pushing to the origin remote. And once work is ready to be merged to the master branch on the origin remote a rebase can be done with the local branch to master and then pushed to the origin remote.

Below shows the default git configuration before and after adding another remote called `dev`.

## Adding Alternate Remote

```
 > more .git/config 
[core]
        repositoryformatversion = 0
        filemode = true
        bare = false
        logallrefupdates = true
        ignorecase = true
        precomposeunicode = true
[remote "origin"]
        url = git@github.com:brennanMKE/MessingWithGit.git
        fetch = +refs/heads/*:refs/remotes/origin/*


 > git remote add dev git@github.com:brennanMKE/MessingWithGit.git
 > more .git/config 
[core]
        repositoryformatversion = 0
        filemode = true
        bare = false
        logallrefupdates = true
        ignorecase = true
        precomposeunicode = true
[remote "origin"]
        url = git@github.com:brennanMKE/MessingWithGit.git
        fetch = +refs/heads/*:refs/remotes/origin/*
[remote "dev"]
        url = git@github.com:brennanMKE/MessingWithGit.git
        fetch = +refs/heads/*:refs/remotes/dev/*
```

Specifically the following command adds the alternate remote.

`git remote add dev git@github.com:brennanMKE/MessingWithGit.git`

## Using Multiple Remotes

Fetching from all remotes can be done with the `--all` switch for the `fetch` command. Each remote will be fetched to sync the local repository. Fetching does not change the working folder as a pull does.

```
 > git fetch --all
Fetching origin
Fetching dev
```

Pushing can be done to a specific remote and branch with the following commands.

`git push remote origin master`

`git push remote dev feature-1`
