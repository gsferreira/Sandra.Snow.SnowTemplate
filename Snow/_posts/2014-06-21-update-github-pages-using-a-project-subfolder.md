---
layout: post
title: Update GitHub Pages using a project subfolder
---

Do you have a project in GitHub and you are tired of manage the *gh-pages* branch manually?! If so, stay tuned because that can be pretty simple.

I used to make a full copy of the master repository into the *gh-pages* using the *rebase* command, but this brings a lack of organization because it's difficult don't mix the source  code and the web pages files.
<!--excerpt-->

<iframe src="//giphy.com/embed/upvM3uYBjh6ww/mp4" width="500" height="378" frameBorder="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>



This is the process that I used to update the full branch:

    git checkout gh-pages // go to the gh-pages branch
    git rebase master // bring gh-pages up to date with master
    git push origin gh-pages // commit the changes
    git checkout master // return to the master branch

Recently I re-organize my repository to have a *docs* subdirectory, on the master branch, where I put the files required for web pages and with the following command I did some magic:

    git subtree push --prefix docs origin gh-pages // Replace 'docs' by your folder name

Now, the *docs* folder is the root directory of gh-pages branch.

This seems pretty simple, but in the process I found some troubled waters. So, I leave the details here, in case you get the same problem.

In my first tries I got the following error:

    ! [rejected]        1835ac01fe63c030216c22d3d834366d5e2a854r -> gh-pages (non-f
    ast-forward)
    error: failed to push some refs to 'https://github.com/gsferreira/myrepository.
    git'
    hint: Updates were rejected because a pushed branch tip is behind its remote
    hint: counterpart. Check out this branch and integrate the remote changes
    hint: (e.g. 'git pull ...') before pushing again.
    hint: See the 'Note about fast-forwards' in 'git push --help' for details.

If you want to get rid of this error, I suggest that you delete your gh-pages branch and then recreate it before execute the *git subtree* command.

How to delete a branch? 
    
    git push origin :gh-pages

I hope this helps you.