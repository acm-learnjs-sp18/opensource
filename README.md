# Learn.js: Open Source + Git

## Resources

- [Slides](https://docs.google.com/presentation/d/1QcK2dQt-mM8G6J0xA_rQG2MCJYUYlmeghNFXoBevcOs/edit?usp=sharing)
- [Super Super Cool, Interactive Website To Learn Git](https://learngitbranching.js.org/)

## Getting Started

To follow along with the rest of this README, please download this repository by clicking that bright green button up there that says "Clone or download." It'll give the option to "Download ZIP" on the bottom of the popup, so just click that and save it somewhere easily accessible on your computer for the remainder of the workshop.

**![img](https://lh3.googleusercontent.com/QAgxKhaUVanRcpz5vckrySOmDEzh6GvcmeZCy_rKPcKCdkKOoxpx9KkkMnp9HNCxSHivh48tkWmtfmsBEnqs8M73ARgYFCglx9V5zYe5KstTuUW4OrfQYV6X5ezVDdpD5GKwvQBW)**

Now you should have a file on your computer titled `opensource-master.zip`. Double-click to expand the ZIP file and you'll see a new directory titled `opensource-master`.

Inside this file are two files: `NewFile.txt` and this README `README.md`. Only `NewFile` is relevant to this workshop, since you're already reading the README!

Now that you have all the required files, let's get started with some Git!

## Git Init

Move the `NewFile.txt` file into a **new folder**. I am going to call mine `myfolder` for the rest of this workshop, but feel free to name yours whatever you want and remember to replace "myfolder" with whatever you named *your* folder (this is the most confusing part of this workshop, I promise).

**I recommend you save the folder on your desktop.** (You can delete it after the workshop.) It'll make this next bit much easier, but if you know your way around the Terminal, then place it wherever is easiest to find.

So, now we have `myfolder` with nothing else but `NewFile.txt` inside it:

**![img](https://lh5.googleusercontent.com/t5Nvbp_JUkb9Q4oUFSF0oCDXxALW8-ag0LSF3etSeFzhxM_2SxYcUGdTr5oRTCQxf19ppi0K3vs0dn_X2snQHkD_9DEU14dTmNI4IInwgFT3BLSx7FMGuskKR08f4LaGFlq6jjik)**

See, on my Desktop I have a folder called `myfolder` with `NewFile.txt` inside. 

Now it's time to actually bring the Git into play. 

Open up your "Terminal" application. It should bring you to a screen that looks like this:

**![img](https://lh3.googleusercontent.com/kPGO20gUShJ3aSh7jOY7FkXm_EvhDsNbFQikOi5zoD9hav0_WdI7oR81C7gLMM4jGOz5j8myMZnmsnOQA-IelRpQK2S89rPMJ7mXJXXInL_Lqhu0cPW_-HRqkXi2BWrP-mhCRMdD)**

with your name instead of mine, of course. If you saved `myfolder` on your Desktop, then simply type in:

```bash
cd Desktop/myfolder
```

You should notice your path change (*i.e.* instead of saying `~ dustinnewman$` it should say `myfolder dustinnewman$`). If you didn't place `myfolder` in your Desktop, use the `cd` command to navigate to the correct place. As long as you end up in `myfolder`, we're good!

Finally, here it is! Our very first Git command. Scary right? Actually, it's only seven letters! In your Terminal, type in:

```bash
git init
```

If it was a success, it should print out:

```
Initialized empty Git repository in /Users/dustinnewman/Desktop/myfolder/.git/
```

This basically adds a directory called `.git` with a bunch of useful Git-related stuff inside to keep track of all your files.

## Git Commits

One of the most basic and fundamental ideas in Git is that of a "commit": a particular snapshot of code saved and backed up (or *committed*) to a project you're working on.

Before we get into commits though, let's first check up on the status of our little project. Inside the Terminal, enter:

```bash
git status
```

And it should print out something like this:

```bash
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	NewFile.txt

nothing added to commit but untracked files present (use "git add" to track)
```

Let's break this down a little bit.

First, we're on the "branch" master. A branch is just one version of code. Think of branches as paths through a forest. Each path has its own twists and turns and yet they all come from the same place (*i.e.* build from the same starting codebase). A Git convention is to call the most stable and finished branch the "master" branch. 

Second, we're on our initial commit. Basically, we haven't made any commits yet. All we've done is setup a git repository and told our computer "Hey! `myfolder` is a Git project."

Lastly, we have our "untracked files." This one takes a little more detail to explain, but don't worry, you'll git it!

### To Track or Not To Track...

That is the question. So, we've set up our Git directory, told our computer that `myfolder` is a Git project, but we haven't actually told Git what to **do** yet. To start off, we should probably tell it what files it should actually "track."

To "track" something just means that Git will keep an eye on that file and, if it changes, take note of those changes so that we can update and commit to our branch (our version of the code). If Git isn't tracking a file, then we change it all we want, but it won't care. 

More concretely, we've set up `myfolder` to be a Git project, but we haven't told it that it should be watching `NewFile.txt`. And so, `NewFile` is deemed "untracked" (*i.e.* Git knows that it's there, but it's not particularly concerned about it).

So, let's take care of that! How do we tell Git that it should start tracking `NewFile` for changes? Well, we're going to use a command called `git add` to *add* `NewFile` to the files Git is tracking.

Type in:

```bash
git add NewFile.txt
```

It may seem like nothing happened, but type `git status` in again and:

```bash
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   NewFile.txt
```

Whoo! We have a new file called, fittingly, `NewFile.txt` and it will be included in the next commit.

Speaking of which, let's get to that!

### If The Change Doesn't Fit, You Must Commit

Well, it's all set up for us now; the only thing left to do is actually commit our new file `NewFile.txt`. Easily enough, just type in:

```bash
git commit -m "Added NewFile"
```

`git commit` is the command you'll use to, well, commit and the extra `-m "Added NewFile"` is an option that we're going to use for this workshop so you don't have to mess with the Terminal text editors. The "Added NewFile" bit is called your *commit message* hence the little `-m` flag ("m" for message).

Now if we type in `git status`, we should get:

```bash
On branch master
nothing to commit, working tree clean
```

And our work here is done! There's nothing left to commit.

### Let's Cause Some Trouble

Except, well, this is pretty useless isn't it? We haven't actually *done* anything like we would change actual code.

So, let's get to that!

Open up `NewFile.txt` in some sort of text editor and make whatever changes you want. I'm personally just going to add several iterations of "EDIT" on a second line, but it's up to you. Just make sure you actually *do* change something.

Now typing in `git status` will print the following:

```bash
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   NewFile.txt

```

(If you get something underneath about an untracked file named `NewFile.txt~`, just ignore it or delete it if you want.)

Once again, `NewFile` has changed but is **not** added to our next commit. Let's change that.

But this time, let's do it a little more efficiently and combine `add` and `commit` into just one command (just one!).

```bash
git commit -am "Edited NewFile"
```

This is just like the `git commit -m` except we have the additional tag of `-a` which adds all tracked files to the commit and then actually commits those files. (Untracked files like `NewFile.txt~` have to be added explicitly luckily.)

## It's Good to Branch Out

So this is pretty cool if you only ever work by yourself, but what if you and your friend *both* wanna work on the same project? Sure, you could just email the code back and forth, but if your project gets any bigger than a few files, that's going to be a nightmare before you know it. Especially if you're working across time zones or simultaneously.

Enter: branches.

Like we said earlier, branches are just different versions of the same codebase. Usually, branches are made as "feature branches" or branches that implement some cool feature or fix a bug and then need to be reconciled with the original master branch again. But more on that later!

For now, let's just make our first branch called `undo-edits` whose purpose is to undo whatever unsightly edits we made in our last commit. To do this, type:

```bash
git branch undo-edits
```

And then

```bash
git checkout undo-edits
```

(In case you couldn't tell, Git is big on productivity and making things faster, so a more common way of creating a new branch and then simultaneously switching to that branch is

```bash
git checkout -b undo-edits
```

where the `-b` stands for "branch.")

Ok, cool! Now we have our very own branch `undo-edits`. Time to do that super important and very tiring work of undoing those edits we made. So, go into your text editor and try to put back the original content to the best you remember. (It doesn't actually matter if you put it back to the original; luckily, Git is very smart. Just make sure to change it somehow from the way it is now so Git picks up on the changes.)

After you've done your heroic restorative work on `NewFile.txt`. Let's 

```bash
git commit -am "Undid edits"
```

To let everyone know that we've done our job.

Now, we want to merge this change back into master, so no one else gets the bad, edited version of `NewFile`. To do this, let's

```bash
git checkout master
```

"Checkout" is how you switch to a new branch in Git. Why it isn't `git switch` I'll never know.

Time to merge those changes we made in `undo-edits`! To merge, it's just

```bash
git merge undo-edits
```

And you should get something printed out like this:

```bash
Updating 47143ea..74f1aad
Fast-forward
 NewFile.txt | 3 +--
 1 file changed, 1 insertion(+), 2 deletions(-)
```

The exact numbers will differ between people, but the important thing is that if you view `NewFile.txt`, it should look like the original again.

Great! Now that we have our super sick and hella useful product, it's time to upload it to the Internet so everyone can see our hard work and use it to build other super, even sicker things!

## GitHub: The Hub of Gits

GitHub is almost synonymous with Git at this point, but it's important to remember that the two are not at all the same thing. "Git" is simply the software, the system of version control that we've been using. As you can tell from the above, we can use Git completely independently of GitHub. However, it wouldn't be nearly as useful because...

"GitHub" is the largest host of Git projects in the world right now, home to many of the companies and products you know and love. They use Git to promote open source software and get the tech community to work together to build some pretty amazing things.

However, even though the two are independent of one another, they are both most useful when used together, so let's get to that!

### Starting a Repo

A "repo" (pronounced ree-po, rhymes with "depot") is just short for "repository," which is just another way to say a folder, specifically a folder for a project that uses Git to keep track of its code. Which is luckily just what we have inside `myfolder`!

Go to [GitHub.com](https://github.com/). If you have an account but you're not particularly *active*, you'll see something like this:

**![img](https://lh5.googleusercontent.com/X8Hqk09Heg8AVtm1SwL-3WhWZgCx4ivr2PjUIzmbrm6l62IdflDJnHeVa7XnBEEQAfFoxqrN1K0TtBtzERgfQp0W1Nt_xUlAS7-k762t2Ba_x_66SlVPDwUnw8MpcHBS2oSti4Hp)**

(If you're more active on GitHub, your home screen will be populated with various updates about the repos you're contributing to). If you don't have an account yet, please sign up for one! The rest of the workshop from here on requires it.

Up in the top right corner, next to your profile picture, should be a little plus-sign icon. Click on it to see the option "New repository."

**![img](https://lh4.googleusercontent.com/dj_dSliv9rGoEW1X3kJloigp5pTMIMSxSPiteDMzB8roa-IQavSyhF4nqFr-pLVYacIgbODjhRexiaCbk4-lSULo6A06KtsDlyTZiaJ1nj67PtFPrS55LR2wp3M8foYoj-9MZ8R4)**

Once you click on that, you'll be taken to this screen

**![img](https://lh5.googleusercontent.com/b5TZbnqZbyE58_Do_BxZ6ZMtWNizr6lbYDQTXnNTNKucDKNu50RUY9avHmXH-lSCN0HoxSkw7B6cPUY4HQgsmZFIEC6tZC8I6qelXVLucw6JO3pQ4dnk8ccz9PhzPNXl6wnIPcvX)**

where you can name your repo and set various different settings for it. For now, we'll just name it `myfolder` and leave everything else default.

Click the big green button that says "Create repository."

Congrats! You just created your very first GitHub repo, welcome to the club! :octopus::cat:

### Adding An Origin

Now, it's time for something a little more complicated. We have this repo set up through GitHub but do we actually connect it to the one we have on our computer? 

Luckily, GitHub makes this really easy. Even if this page looks overwhelming, don't worry! We only actually need **two commands**.

**![img](https://lh3.googleusercontent.com/f_IVXy1_r9UpAyaj4zX32NJCPXTRwcv4YdmGZy81aeR94Uu9aWTgoNLPGTAG0jjPQLdcnMZuqKejdPN9gFG7U7EgkndUGWiSnZgk3ETwjPJnMv5Chp0p-3gWDHewY1BvTGUb2cyM)**

We're going to use the `git remote add` and `git push` commands to set up our "local" repo (*i.e.* `myfolder`) onto GitHub's version of it.

In your Terminal, type:

```bash
git remote add origin https://github.com/your_name/myfolder.git
```

This will add something called a "remote" to your repo and this "remote" will be called "origin." A *remote* is just another way of saying "something you upload your code to." And since this is the first remote we're adding to `myfolder`, it's just convention to name it "origin," although the actual name is arbitrary. 

After you've added the remote, it's time to use it! Let's finally push to our remote

```bash
git push -u origin master
```

It may take a little bit, but once it's done, you'll get something like this:

```b
To https://github.com/your_name/myfolder.git
 * [new branch]      master -> master
Branch master set up to track remote branch master from origin.
```

Ta-da! Refresh the page to see your new repo look something like this:

**![img](https://lh4.googleusercontent.com/d9oELpNjxwZtjYAqHYX3lhhlVq2vzOTLyzFUgIT7rvTAMHVu9aBktoGw_t38kCx7V06EEKZYHUTf5aC46bdKw_HUnT_dOOkdzOMGOXBz09Ta8xr3GMCJUoaG8z4AIyGFPIYYZbza)**

Now your code is up on the Internet for anyone to see and use, which is the very spirit of open source. Speaking of which...

## Cloning (No, Not THAT Kind)

While we hope this workshop has been helpful, it's also important to know that a lot of your time on GitHub and in the open source community in general will be working on *other people's* code and not necessarily your own. But how do you set that up exactly?

Glad you asked!

Let's navigate to a [really cool open source project for Node.js](https://github.com/bitinn/node-fetch) that aims to make web connections faster in Node. 

Let's say we were interested in this project and think we could help them out! Well, the first thing we'd wanna do is click on the big green button again and this time, instead of "Download as ZIP," we can click the Git Expert™ option, which is to **clone**. 

To *clone* a repo is just to download its contents on your computer (your "local machine"), complete as a Git project right from the start. You don't have to worry about `git init` or downloading the files or anything like that. It's all right there.

Ok, so let's say we want to clone this repo.

**![img](https://lh4.googleusercontent.com/2_yILubiPXhd4bZqLvtnLgLCFarfSUAibeFtT9S-26BPrI1oPD7ZwiTIpbqj5RsmIoe_K3xvEbYfmIatsMbabwwhG7WdHxXxwUK1O7X2--yeY8_ynaHrwfNX_1ZbTQHSz6Lh8VKZ)**

Well, lucky once *again* for us, GitHub provides a super easy way to do just this. Click on that little clipboard icon to get this link:

```
https://github.com/bitinn/node-fetch.git
```

Now, go back to your computer and find somewhere you want to put this project. Don't worry! It's a small file size!

**Note:** Don't create a specific folder for this project. For example, if I wanted node-fetch on my Desktop, I <u>wouldn't</u> create a folder called `node-fetch` inside my Desktop. Instead, I would just navigate to my Desktop inside the Terminal and do the following.

Now, in your Terminal, just type in 

```bash
git clone https://github.com/bitinn/node-fetch.git
```

And Git will create a folder called `node-fetch` with all the files and configurations you need to start contributing to your very first open source project!

*Thanks for reading!* We hope you enjoyed our introduction to open source and Git/GitHub. Now, go git down to business! 