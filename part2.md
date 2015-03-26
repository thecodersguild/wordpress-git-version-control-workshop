# Repository Hosting Services
A repository hosting service allows you to host your repository in the cloud so that your team can sync up with it.  These are the two most popular: 

## GitHub
[GitHub](https://github.com/) provides unlimited public repositories, but [charges based on the number of private repositories](https://github.com/pricing) that you have. GitHub tends to be the best place to host open source repositories and get feedback from an active community of developers.

[Create a GitHub account](https://github.com/join)

## BitBucket
[BitBucket](https://bitbucket.org/) provides unlimited public and private repositories, but [charges based on the number of users](https://bitbucket.org/plans) that have access to your repositories.  BitBucket tends to be the best place to host private repositories for personal use or for client work.

[Create a BitBucket account](https://bitbucket.org/account/signup/)

# Repository Access

## HTTPS
When using HTTPS to push code or clone a private repository, it is necessary to provide your username and password.  As such, it can be helpful to either cache or permanently store your credentials.

### Caching Credentials

Run `git config --global credential.helper cache` once and git will cache your credentials for a set period of time.  

You can configure how long credentials will be cached by running `git config --global credential.helper "cache --timeout=3600"`, where `--timeout` is the time in seconds.

GitHub provides [additional directions](https://help.github.com/articles/caching-your-github-password-in-git/#platform-all) on how to further integrate with features of your operating system, but these are entirely optional.

### Permanently Storing Credentials

Run `git config --global credential.helper store` once and git will request your username and password the first time and store it in a `.git-credentials` file in your home directory.  Once saved, git will automatically use the stored credentials in the future.

To disable this functionality, just run `git config --global --unset credential.helper`.


## SSH

When using the SSH option for accessing a repository, it is necessary to setup SSH keys.  This is the most secure way of working with repositories.

###Generating SSH Keys

GitHub provides excellent instructions on [how to generate SSH keys](https://help.github.com/articles/generating-ssh-keys/#platform-all).

# GitFlow
[GitFlow](http://nvie.com/posts/a-successful-git-branching-model/) is a branching model introduced by Vincent Driessen about 5 years ago.  Since, he has also created the [GitFlow collection of extensions](https://github.com/nvie/gitflow) that makes it even easier to utilize his branching model.

A key concept of this branching model is that the `master` branch is always production ready.  Any development that takes place occurs on the `develop` branch.  Commits to the `master` branch are tagged with a version based on [Semantic Versioning](http://semver.org/).

# SourceTree
[SourceTree](http://www.sourcetreeapp.com/) is a tool that provides a graphical user interface for git.  SourceTree ships with GitFlow installed and provides a user-friendly interface for using this branching model.

# Git and WordPress
When using git to version a WordPress project it is important to know what needs to be versioned and what doesn't.

If you are creating a theme or plugin, then all of your code should be versioned.  If you are versioning an entire WordPress site, it is important to version your custom code, but not necessarily third party code, such as WordPress core and third party plugins.  While you absolutely can version everything, there is really no need to version an entire third party codebase.

However, it is important to realize that while you don't need to version an entire third party codebase you should definitely track what version of the third party codebase you are using.  While that sounds contradictory, the difference is quite significant in implementation.

You shouldn't version your database, just your code.  Also, you probably shouldn't version your uploads directory since that is considered to be more related to data than the actual code base.