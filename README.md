Git Sandbox
===========

## Overview

Git is a practical thing. Maybe that's the reason why it's at times difficult to understand its formal documentation.

To find my way around a tricky Git use case, I don't rely solely on the docs. I have a quick glance at the docs to get a general idea, and then **try that case in sandbox environment** right away.

It's not always easy to create a multi-user Git sandbox environment manually, it takes quite an effort each time. Also in course of our experiments we often want to delete it all and start over, which adds a bit of pain.

Thus, step by step, **Git Sandbox** was born.

## What's Git Sandbox?

Git Sandbox is a tool, which allows you to **conduct Git experiments** acting as several developers at once, do it **fast** and with **minimal effort**. The idea behind it is:

> **If you don't know how Git will behave in a particular tricky situation, go try it in a sandbox NOW.**

Don't put it off, don't try to work around it by avoiding aspects you don't know well. In other words &mdash; **just go try it**. It won't bite, it'll take you just a few minutes of learning, but you'll gain solid knowledge and confidence which will be with you forever.

## Setup

Download `PS1` and `Sandbox` into an empty directory, do a `chmod +x Sandbox`, run `./Sandbox setup`. Then follow the on-screen help. A complete example follows.

## Example: Simulating a merge conflict

1. Create an empty directory and step into it:

    ```sh
    $ mkdir git-xperiment
    $ cd git-xperiment
    ```

2. Download the sandbox scripts, do the setup:

    ```sh
    $ curl https://raw.githubusercontent.com/dadooda/git-sandbox/master/{PS1,Sandbox} -OO
    $ chmod +x Sandbox
    $ ./Sandbox setup
    $ . PS1
    ```

4. Now that everything is ready, start playing with Git. Initialize the repo:

    ```sh
    git-xperiment$ ./Init
    ```

5. Acting as developer Alice, start writing a poem. Notice how **shell prompt changes** as you step in and out developers' working copies:

    ```sh
    git-xperiment$ ./Clone alice
    git-xperiment$ cd alice
    alice[]$ echo "The poem" > poem.txt
    alice[]$ git add . && git commit -a -m "Update" && git push origin master
    ```

6. Connect one more developer, Bob. Let him add a line:

    ```sh
    alice[master]$ cd ..
    git-xperiment$ ./Clone bob
    git-xperiment$ cd bob
    bob[master]$ echo "Mary had a little lamb" >> poem.txt
    bob[master]$ git add . && git commit -a -m "Update" && git push origin master
    ```

7. Back in Alice's working copy, add a line, commit, then fetch and merge:

    ```sh
    bob[master]$ cd ../alice
    alice[master]$ echo "Mary had a little ham" >> poem.txt
    alice[master]$ git add . && git commit -a -m "Update" && git push origin master
    error: failed to push some refs to 'git-xperiment/.repo.git'
    hint: Updates were rejected because the tip of your current branch is behind
    ...

    alice[master]$ git fetch
    alice[master]$ git merge origin/master
    Auto-merging poem.txt
    CONFLICT (content): Merge conflict in poem.txt
    Automatic merge failed; fix conflicts and then commit the result.
    ```

The conflict! That's what we wanted, and we got it. Proceed further to your liking.

## Cheers!

Feedback of any kind is highly appreciated.

&mdash; Alex Fortuna, &copy; 2015-2020
