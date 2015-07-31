Git Sandbox
===========

Overview
--------

Git is a practical thing. Maybe that's the reason why it's at times difficult to understand its documentation.

In my Git practice I don't try very hard to grasp what the docs say. Instead, I pick a particular case, have a quick glance at the docs to have a general idea, and then **try the case in a sandbox**.

I started by creating repositories and working copies by hand, which took a quite an effort each time. Considering the fact that during experiments you often need to delete everything and start anew, that was particularly painful.

Thus, step by step, **Git Sandbox** was born.

What's Git Sandbox?
-------------------

Git Sandbox is a tool, which allows you to **conduct Git experiments** pretending to be several developers at once, do it **fast** and with **minimum effort**. The idea behind it is simple:

**If you don't know how Git will behave in a particular situation, go try it in a sandbox NOW.**

Don't put it off, don't try to work around it by avoiding aspects you don't know well. In other words &mdash; **just be brave enough to try it**. It won't bite, it'll take you 5 minutes, but you'll gain solid knowledge and confidence which will be yours for years.

Setup
-----

Download the files `PS1` and `Sandbox` into an empty directory, do a `chmod +x Sandbox`, run `./Sandbox setup`. Then follow the on-screen help. A complete example follows.

Example: Simulating a merge conflict
------------------------------------

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

5. Predending to be developer Alice, start writing a great poem. Notice how **shell prompt changes** as you step in and out developers' working copies:

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

7. Back to Alice's working copy, add a line, commit, then fetch and merge:

    ```sh
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

Cheers!
-------

Feedback of any kind is highly appreciated.

&mdash; Alex Fortuna, &copy; 2015
