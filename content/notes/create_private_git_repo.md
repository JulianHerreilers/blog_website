---
title: "How to create and maintain a private git repo"
date: 2025-04-28
categories: ["notes"]
tags: ["git"]
summary: "A simple guide for beginners to create and maintain a private Git repository."
hiddenInHomeList: true
---

Summary: I created this for two reasons: 
Firstly, I remember how intimidating it was to create a private git repo when I first had to. Secondly, I am trying to convert some of my non-software friends to use git to maintain their university documents (i.e. thesis drafts) and want to make it as simple as possible.
Git is basically a way to checkpoint and maintain history of the changes in a folder (much like a drive). While it looks complex, I hope to summaries the key concepts and commands to make it as simple as possible.

1. First, ensure you have a [GitHub](https://github.com/) account.

2. Under "Your repositories", select "create repository". Here, give your repo a name (i.e. masters_thesis) and select Private if that is what your require. This will now create a blank repository which functions the same as your drive.

3. Now navigate to the folder which you want to connect. While this can be done with Command Prompt (CMD), I prefer installing [git bash](https://git-scm.com/downloads). Then use ``cd`` and ``ls`` to ensure you are in the correct directory. You can copy the path from File Explorer.

4. Once you are in the directory run ```git init```. You have now created a repository. Running ```git status``` shows you that you have no commits and have a number of untracked files.

5. To add files to track or to save changes simply run:
    ```git add <filename>```

6. Next we are going to commit the added files. This is like an explicit checkpoint/save. A commit requires a save message and is run as follows:
    ```git commit -m "My first commit"```

7. Next run ```git branch -M main``` 

8. Now in order to connect to the blank repository on GitHub we need to add a connection
    ```git remove add origin git@github.com:<username>:<repo_name>.git```
9. Finally run the following to push the changes to the repo. ```git push -u origin main```

10. If you have a private repo, this last step may have failed. This is because you need to have some sort of authentication  to show GitHub that you are a supposed to upload here. Here you need to create an ssh key.

11. Do the following in your terminal to create a key:
- ssh-keygen -t ed25519 -C "your_email@example.com"
- copy the contents of ~/.ssh/id_ed25519.pub **ENSURE YOU USE THE PUBLIC KEY**. You can also open this file in a text editor and copy all the contents.
- In GitHub, under your settings, go to "SSH and GPG keys" and then "New SSH key".
- Give a title such as "laptop_ssh_key". Key type is set to "Autenthication Key" by default and copy the contents into the "Key" field.
- If you have done this correctly, running ```ssh -T git@github.com``` should return ```Hi JulianHerreilers! You've successfully authenticated, but GitHub does not provide shell access.```

12. Now run step 9. again and if you look on the repo page your uploaded files should be there.


From here on it is pretty simple to maintain. Whenever you work on your projects and files and what to save them, simply run the following:
1. ```git add <filename>```
2. ```git commit -m "Saved X on Y - did Z. (I like to add what I plan to do next)"```
3. ```git push```
4. Use ```git status``` to ensure that all your modified and tracked files are committed and saved. If not, repeat steps 1-3 above.
