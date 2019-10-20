# CONTRIBUTING

Azure Active Directory SDK projects welcome new contributors.  This document will guide you
through the process.

### CONTRIBUTOR LICENSE AGREEMENT

Please visit [https://cla.microsoft.com/](https://cla.microsoft.com/) and sign the Contributor License
Agreement.  You only need to do that once. We can not look at your code until you've submitted this request.


### FORK

Fork the project [on GitHub][] and check out
your copy.

Example for JS:

```
$ git clone git@github.com:username/microsoft-authentication-library-for-js.git
$ cd microsoft-authentication-library-for-js
$ git remote add upstream git@github.com:AzureAD/microsoft-authentication-library-for-js.git
```

Now decide if you want your feature or bug fix to go into the dev branch
or the master branch.  **All bug fixes and new features should go into the dev branch.**

The master branch is effectively frozen; patches that change the SDKs
protocols or API surface area or affect the run-time behavior of the SDK will be rejected.

Some of our SDKs have bundled dependencies that are not part of the project proper.  Any changes to files in those directories or its subdirectories should be sent to their respective
projects.  Do not send your patch to us, we cannot accept it.

In case of doubt, open an issue in the [issue tracker][].

Especially do so if you plan to work on a major change in functionality.  Nothing is more
frustrating than seeing your hard work go to waste because of your vision
does not align with our goals for the SDK.


### BRANCH

Okay, so you have decided on the proper branch.  Create a feature branch
and start hacking:

```
$ git checkout -b my-feature-branch
```

### BOOTSTRAP

After you have cloned the repository, run `npm install` in the root folder. This will install the dependencies for all of the libraries and samples in the repo, create linkages between packages that have dependencies on each other, and run the build process for each of the libraries.

To reset each of the libraries, run `npm run clean` in the root folder, which will remove the `node_modules` folders and build files for each repo and sample.

### PRE COMMIT

We will automatically run lint as our pre-commit command. Failing to pass linting will prevent you from pushing up code which will break the build.

```
$ npm run lint
```

This will ensure any changes are consistent with the current code style. We use tslint and you can find a list of linting rules in the tslint.json.

If for some reason you still want to push without fixing the linting errors. You can add the following option to your commit command to [bypass the pre-commit][]:

```
--no-verify
```


### COMMIT

Make sure git knows your name and email address:

```
$ git config --global user.name "J. Random User"
$ git config --global user.email "j.random.user@example.com"
```

Writing good commit logs is important.  A commit log should describe what
changed and why.  Follow these guid elines when writing one:

1. The first line should be 50 characters or less and contain a short
   description of the change prefixed with the name of the changed
   subsystem(e.g. "net: add local address and local Port to Socket").
2. Keep the second line blank.
3. Wrap all other lines at 72 columns.

A good commit log looks like this:

```
fix: explaining the commit in one line

Body of the commit message is a few lines of text, explaining things
in more detail, possibly giving some background about the issue
being fixed,etc.

The body of the commit message can be several paragraphs, and
please do proper word-wrap and keep columns shorter than about
72 characters or so. That way `git log` will show things
nicely even when it is indented.
```

The header line should be meaningful; it is what other people see when they
run `git shortlog` or `git log --oneline`.

Check the output of `git log --oneline files_that_you_changed` to find out
what directories your changes touch.


### REBASE

Use `git rebase` (not `git merge`) to sync your work from time to time.

```
$ git fetch upstream
$ git rebase upstream/v0.1  # or upstream/master
```


### TEST

Bug fixes and features should come with tests.  Add your tests in the
test directory. This varies by repository but often follows the same convention of /src/test.  Look at other tests to see how they should be
structured (license boilerplate, common includes, etc.).


Make sure that all tests pass.


### PUSH

```
$ git push origin my-feature-branch
```

Go to https://github.com/username/microsoft-authentication-library-for-***.git and select your feature branch.  Click
the 'Pull Request' button and fill out the form.

Pull requests are usually reviewed within a few days.  If there are comments
to address, apply your changes in a separate commit and push that to your
feature branch.  Post a comment in the pull request afterward; GitHub does
not send out notifications when you add commits.


[on GitHub]: https://github.com/AzureAD/microsoft-authentication-library-for-js
[issue tracker]: https://github.com/AzureAD/microsoft-authentication-library-for-js/issues
[bypass the pre-commit]: https://git-scm.com/docs/git-commit#Documentation/git-commit.txt---no-verify
