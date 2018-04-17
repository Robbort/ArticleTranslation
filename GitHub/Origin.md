[Link Address](https://help.github.com/articles/why-are-my-contributions-not-showing-up-on-my-profile/)

# Why are my contributions not showing up on my profile?

Your profile contributions graph is a record of contributions you've made to GitHub repositories. Contributions are timestamped according to Coordinated Universal Time (UTC) rather than your local time zone. Contributions are only counted if they meet certain criteria. In some cases, we may need to rebuild your graph in order for contributions to appear.

## Contributions that are counted

### Issues and pull requests

Issues and pull requests will appear on your contribution graph if they were opened in a standalone repository, not a fork.

### Commits

Commits will appear on your contributions graph if they meet all of the following conditions:

> The email address used for the commits is associated with your GitHub account.
The commits were made in a standalone repository, not a fork.
The commits were made:
In the repository's default branch (usually `master`)
In the `gh-pages` branch (for repositories with [Project Pages sites](https://help.github.com/articles/user-organization-and-project-pages/#project-pages-sites))

In addition, **at least one** of the following must be true:

> You are a collaborator on the repository or are a member of the organization that owns the repository.
> You have forked the repository.
> You have opened a pull request or issue in the repository.
> You have starred the repository.

## Common reasons that contributions are not counted

> Notes:

> To appear on your profile contributions graph, co-authored commits must meet the same criteria as commits with one author.
When a pull request is merged and commits are squashed, only the user that merged the pull request and the user that opened the pull request [receive contribution credit](https://help.github.com/articles/viewing-contributions-on-your-profile/). No other contributors to the pull request will receive contribution credit.
When rebasing commits, the original authors of the commit and the person who rebased the commits, whether on the command line or on GitHub, receive contribution credit.

### Commit was made less than 24 hours ago

After making a commit that meets the requirements to count as a contribution, you may need to wait for up to 24 hours to see the contribution appear on your contributions graph.

### You haven't added your local Git commit email to your profile

Commits must be made with an email address that has been added to your GitHub profile in order to appear on your contributions graph. You can check the email address used for a commit by adding `.patch` to the end of a commit URL, e.g. [https://github.com/octocat/octocat.github.io/commit/67c0afc1da354d8571f51b6f0af8f2794117fd10.patch](https://github.com/octocat/octocat.github.io/commit/67c0afc1da354d8571f51b6f0af8f2794117fd10.patch):

> From 67c0afc1da354d8571f51b6f0af8f2794117fd10 Mon Sep 17 00:00:00 2001
From: The Octocat (octocat@nowhere.com)
Date: Sun, 27 Apr 2014 15:36:39 +0530
Subject: [PATCH] updated index for better welcome message

The email address in the `From:` field is the address that was set in the [local git config settings](https://help.github.com/articles/set-up-git/). In this example, the email address used for the commit is `octocat@nowhere.com`.

If the email address used for the commit hasn't been added to your GitHub profile, you must [add the email address](https://help.github.com/articles/adding-an-email-address-to-your-github-account/) to your GitHub account. Your contributions graph will be rebuilt automatically when you add the new address.

> Generic email addresses--such as `jane@computer.local` --cannot be added to GitHub accounts. If you use such an email for your commits, the commits will not be linked to your GitHub profile and will not show up in your contributions graph.

### Commit was not made in the default or `gh-pages` branch

Commits are only counted if they are made in the default branch (usually `master`) or the `gh-pages` branch (for repositories with [Project Pages sites](https://help.github.com/articles/user-organization-and-project-pages/#project-pages-sites)). If your commits are in a non-default or non-`gh-pages` branch and you'd like them to count toward your contributions, you will need to do one of the following:

> [Open a pull request](https://help.github.com/articles/creating-a-pull-request/) to have your changes merged into the default branch or the gh-pages branch.
[Change the default branch](https://help.github.com/articles/setting-the-default-branch/) of the repository.

Changing the default branch of the repository will change it for all repository collaborators. Only do this if you want the new branch to become the base against which all future pull requests and commits will be made.

### Commit co-author doesn't have access to the repository

If a commit was made in a repository that the co-author doesn't have access to, then that commit will not count towards the co-author's contributions.

### Commit was made in a fork

Commits made in a fork will not count toward your contributions. To make them count, you must do one of the following:

> [Open a pull request](https://help.github.com/articles/creating-a-pull-request/) to have your changes merged into the parent repository.
To detach the fork and turn it into a standalone repository on GitHub, contact [GitHub Support](https://github.com/contact). If the fork has forks of its own, let support know if the forks should move with your repository into a new network or remain in the current network. For more information, see "[About forks](https://help.github.com/articles/about-forks/)."

### Commit was made in a pull request that was merged and squashed

Commits made in a pull request that was [merged and squashed](https://help.github.com/articles/about-pull-request-merges/) will not count toward your contributions. Only the user that merged the pull request and the user that opened the pull request receive contributions. No other contributors to the pull request will receive contribution credit.