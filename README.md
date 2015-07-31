Git Sandbox
===========

Overview
--------

Git is a practical thing. Maybe that's the reason why it's at times difficult to understand its documentation.

In my Git practice I don't try very hard to grasp what the docs say. Instead, I pick a particular case, have a quick glance at the docs to have a general idea, and then **try the case in a sandbox**.

I started by creating repositories and working copies by hand, which took a quite an effort every time. Considering the fact that during experiments you often need to delete everything and start anew, that was particularly painful.

Thus, step by step, the **Git Sandbox** was born.

What's Git Sandbox?
-------------------

Git Sandbox is a tool, which allows you to **conduct Git experiments** pretending to be several developers at once, do it **fast** and with **minimum effort**. The idea behind it is simple:

**If you don't know how Git will behave in a particular situation, go try it in a sandbox NOW.**

Don't put it off, don't try to work around the case by avoiding the aspects you don't know well. In other words &mdash; **just be brave enough to try it**. It won't bite, it'll take you 5 minutes, but you'll gain solid knowledge and confidence.

Setup
-----

Download the files `PS1` and `Sandbox` into an empty directory, do a `chmod +x Sandbox`, then run `./Sandbox setup`. A complete example follows.

Example: Simulating a merge conflict
------------------------------------

1. Create an empty directory and step into it:

    ```sh
    $ mkdir git-merge-conflict
    $ cd git-merge-conflict
    ```

Cheers!
-------

&mdash; Alex Fortuna, &copy; 2015
