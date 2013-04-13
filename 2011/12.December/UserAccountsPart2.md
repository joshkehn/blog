{"title":"Server Setup, Part 2: User Accounts", "date":1323797429912}
++++++++++
Back in [Setting Up a Server, Part 1][suas 1] the root user account was used to configure a login and SSH keys. That worked for the example, and truth be told it isn't a horrible way to start working on a server. Root accounts on a Unix system are fully permissioned. You can do anything and everything.[^1] With this amazing power comes some major warnings though.

1. Root has no warnings and no stop signs. Mistyping a command has brought more then one server to it's knees.
2. Leaving root enabled practically begs someone to come and hijack your server.
3. When you futz as root, everything you create becomes root permissioned. This makes it very difficult for other users or non-permissioned users to work with those files.
4. Use of `sudo` is easier to control then access to the root account.

The simplest way to remove most of these concerns is to setup other user accounts and add them to the list of `sudoers`. 

First step is to create the user account. Obviously the root account will be used to create this account. 

    root@junk:~# adduser josh
    Adding user `josh' ...
    Adding new group `josh' (1000) ...
    Adding new user `josh' (1000) with group `josh' ...
    Creating home directory `/home/josh' ...
    Copying files from `/etc/skel' ...
    Enter new UNIX password: 
    Retype new UNIX password: 
    passwd: password updated successfully
    Changing the user information for josh
    Enter the new value, or press ENTER for the default
        Full Name []: 
        Room Number []: 
        Work Phone []: 
        Home Phone []: 
        Other []: 
    Is the information correct? [Y/n] Y

All looks good, let's try running some of our commands.

    root@junk:~# su josh
    josh@junk:/root$ sudo tail -f /var/log/apache2/error.log
    [sudo] password for josh: 
    josh is not in the sudoers file.  This incident will be reported.

This is a permission error when the user you're logged in as isn't listed in the `/etc/sudoers` file. First open the file for editing.

    root@junk:~# vim /etc/sudoers

Now you could also use `visudo` but I prefer to not mess with it. You will see the following lines:

    # User privilege specification
    root    ALL=(ALL) ALL

Duplicate the root line (`yy`) and put a copy after it (`p`). Change `root` to `josh` (or whatever username you picked). 

    # User privilege specification
    root    ALL=(ALL) ALL
    josh    ALL=(ALL) ALL

Save the file (`:wq`). You will now be able to run sudo commands from that user.


    root@junk:~# su josh
    josh@junk:/root$ sudo tail -f /var/log/apache2/error.log
    [sudo] password for josh: 
    […]

Don't forget to copy the `authorized_keys` file. In this case it's best to move it (prevent direct root access) and change the root password as well.

    josh@junk:~# sudo mv /root/.ssh/ ./ && sudo chown -R josh .ssh/
    josh@junk:~# sudo passwd root
    Enter new UNIX password: 
    Retype new UNIX password: 
    passwd: password updated successfully

Now you have a new non-root account you can use for standard logins, with `sudo` permissions so you don't have to touch the root account. The keyfiles have been moved and the root password changed. Install [fail2ban][f2b] if you like.

*** 

That wraps up setting up user accounts. Here is what I'm planning on writing as a series overview:

1. [Basic server prep][suas 1]
2. [Setting up a user account / sudoers permissions][suas 2]
3. Introducing aptitude / package management
4. Setting up Apache
5. Setting up PHP and MySQL
6. Adding additional sites to apache
7. Useful Apache modules
8. Python, Ruby, and Node.js


[^1]: I had a good deal of fun spinning up a server only to run `rm -rf /` on it.

[suas 1]: http://joshuakehn.com/2011/11/30/Setting-Up-a-Server-Part-1.html
[suas 2]: http://joshuakehn.com/2011/12/13/Server-Setup-Part-2-User-Accounts.html
[f2b]: http://www.fail2ban.org/wiki/index.php/Main_Page