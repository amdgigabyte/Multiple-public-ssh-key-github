MULTIPLE PUBLIC SSH KEY ON YOUR MAC OSX
=======================================

Create your ssh keys
--------------------

First you need to create your two ssh key:

    $ ssh-keygen -t rsa -C "test1@test.com"
    $ ssh-keygen -t rsa -f ~/.ssh/id_rsa_OTHER_LABEL -C "test2@test.com"

Note: You can use any name for your public second key


Attach to github
----------------

Login in each github account and attach your keys respectively:

    $ vim ~/.ssh/id_rsa[YOUR_NAME].pub

Copy and paste into the public key field at github page

git-hub doc
http://help.github.com/mac-set-up-git/


Create a ssh config file
------------------------
Well, we create two differents ssh keys and attach respectively in github.
Now, we have to create a way to identify the differents github accounts.

Create a config file

    $ touch ~/.ssh/config
    $ vim ~/.ssh/config

Example:

    #Default GitHub
    Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa
    #Default GitHub
    Host github-company
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa_OTHER_LABEL

And save the changes.

How does it works?
------------------

Now, if you want to create a new project, you have to specify the HOST name in the
add remote origin step.

Example

    $ git init
    $ git commit -m"firt commit"

If you want to use your default ssh key( Github ),, you should write this:

    $ git remote add origin git@github.com:Company/testing.git

Otherwise, if you want to use the other ssh key write something like this:

    $ git remote add origin git@github-COMPANY:Company/testing.git

:)

