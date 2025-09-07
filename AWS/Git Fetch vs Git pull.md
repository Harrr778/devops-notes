## Git fetch and git pull basics[](https://about.gitlab.com/blog/2024/09/24/git-pull-vs-git-fetch-whats-the-difference/#git-fetch-and-git-pull-basics)

Git fetch and git pull are both Git commands used to retrieve update information from a remote repository. So, how do they differ? Git fetch downloads the changes from the remote repository to the local repository but does not make any changes to the current working directory. Since the changes are not merged into the local branch, you can check the changes from the remote repository without interrupting your current work. On the other hand, git pull retrieves the latest changes from the remote repository like git fetch, but it also automatically merges those changes into the current branch. In contrast to git fetch, git pull directly applies the changes from the remote repository to the local working directory.

## What is git fetch?[](https://about.gitlab.com/blog/2024/09/24/git-pull-vs-git-fetch-whats-the-difference/#what-is-git-fetch%3F)

The git fetch command retrieves the latest commit history from the remote repository, but it does not affect the local working directory. Even after fetching remote changes, they are not reflected in the local branch. It is primarily used when you want to retrieve the latest status from the remote repository and review the changes before they are reflected in the local repository. To apply the retrieved changes to the local branch, you need to manually run git merge or [git rebase](https://docs.gitlab.com/ee/topics/git/git_rebase.html).

## What is git pull?[](https://about.gitlab.com/blog/2024/09/24/git-pull-vs-git-fetch-whats-the-difference/#what-is-git-pull%3F)

The git pull command combines `git fetch` and `git merge` (or `git rebase`) into a single command. This allows you to fetch changes from the remote repository and automatically integrate them into the current local branch.

While git fetch retrieves changes from the remote repository without applying them to the local branch, running git pull automatically integrates the changes from the remote repository into the local branch.

Git pull is suitable for quickly reflecting remote changes in the local branch, but it can lead to conflicts, so caution is needed, especially when working with multiple people.

## When to use git fetch[](https://about.gitlab.com/blog/2024/09/24/git-pull-vs-git-fetch-whats-the-difference/#when-to-use-git-fetch)

Git fetch is a command used to retrieve the latest information from a remote repository. The retrieved information is not directly reflected in the local branch. Using git pull will reflect all remote branches, including incorrect or problematic ones, in the local branch.

When changes are made simultaneously on both remote and local branches, or when there are new users on the team, it is safer to use git fetch to retrieve the remote branch contents first and then perform merge or rebase.

## When to use git pull[](https://about.gitlab.com/blog/2024/09/24/git-pull-vs-git-fetch-whats-the-difference/#when-to-use-git-pull)

Git pull is a command that performs more processes compared to git fetch. Git pull can perform both git fetch and additionally execute git merge or git rebase. For this reason, git pull is recommended when you want to quickly reflect changes from the remote repository in the local branch.

## Git fetch and git pull FAQs[](https://about.gitlab.com/blog/2024/09/24/git-pull-vs-git-fetch-whats-the-difference/#git-fetch-and-git-pull-faqs)

### What is the difference between git pull and git fetch?[](https://about.gitlab.com/blog/2024/09/24/git-pull-vs-git-fetch-whats-the-difference/#what-is-the-difference-between-git-pull-and-git-fetch%3F)

Git pull is a command that performs git fetch followed by git merge or git rebase. While git fetch does not affect the local repository, git pull automatically synchronizes changes from the remote repository with the local repository.

### What precautions should be taken when using git pull?[](https://about.gitlab.com/blog/2024/09/24/git-pull-vs-git-fetch-whats-the-difference/#what-precautions-should-be-taken-when-using-git-pull%3F)

When executing git pull, there may be conflicts between remote and local changes. Merge conflicts are particularly likely to occur, so if conflicts arise, they need to be resolved manually. Additionally, using git pull --rebase allows you to incorporate the latest changes while performing a rebase.

### What is git fetch used for?[](https://about.gitlab.com/blog/2024/09/24/git-pull-vs-git-fetch-whats-the-difference/#what-is-git-fetch-used-for%3F)

Git fetch is useful for checking and retrieving the latest status of the remote repository. However, the changes retrieved are not automatically reflected in the local branch; git fetch is used to synchronize the local and remote repositories.
