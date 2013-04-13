{"title":"Setting Up a Server, Part 1", "date":1322681765000}
++++++++++
<p class="note">
This is the first in a multi-part series I am writing on basic server setup and troubleshooting. Anyone wishing for a specific aspect covered is encouraged to contact me.
</p>

Starting a server from scratch can be a daunting task for those that have never done it before. It's not a complex task, but it depends a lot on being comfortable making a few mistakes and searching a bit for help with the sticky points. There are a few skills that will help this process along:

1. Terminal proficiency. Being comfortable with a command line would be helpful. Actually knowing how to use `vim` or how to navigate around in the shell would be invaluable.
2. Mindset for tinkering. Not all of this is cut and dry. What works on Ubuntu 10.04 LTS may not work on Ubuntu 11, much less CentOS.
3. Previous Apache knowledge is also great.
4. Exposure to Linux. Linux is the dominant server flavor today. Previously using Ubuntu or Fedora will help you understand where some things are going as the setup proceeds.

First things should come first. A server is needed that we can play with. The easiest thing to do here is sign up for one of the many cloud hosting sites. Amazon offers a suite of free AWS services if you've never had an account with them before. I tend to recommend [Rackspace Cloud Hosting][rackspace] because it's extremely cost effective and the control panel makes it dead simple to spin up and spin down servers at will.

<p class="note">
There are a few different distributions that one could start with. Enterprise folks will no doubt be leaning towards Cent / RHEL because it's familiar. I will be using Ubuntu 10.04 LTS for everything in this guide, with followups for other OSs if the desire is there.
</p>

Start a server from your desired control panel, using a basic image without anything on it. Just the operating system. You will either set or be given a password for the root user. The root users is god on your computer. It can touch and modify anything. I will be using this user to setup our stuff, but in a production / public environment you should setup a separate main user with sudo permissions. That will be covered in the next part.

Here's what you'll need to continue:

1. The server's IP address
2. root user's password

SSH keys and a proper hosts file make life simpler whether managing one server or a dozen servers. SSH keys can be reused among multiple servers and other systems, like GitHub. If you don't have an SSH keypair setup already it is easy enough to make one.

    $ ssh-keygen
    Generating public/private rsa key pair.
    Enter file in which to save the key (/Users/josh/.ssh/id_rsa):
    Enter passphrase (empty for no passphrase):
    Enter same passphrase again:
    Your identification has been saved in id_rsa.
    Your public key has been saved in id_rsa.pub.
    The key fingerprint is:
    ea:f9:03:e7:1c:64:c3:cd:45:e7:f5:36:d8:8c:39:dd

Unix derived systems will "shadow" the password being entered. No characters will be displayed and no feedback given. This is expected behavior, and your password **is** being recorded. Entering the password twice helps mitigate any misplaced fingers while typing.

Assuming you used the default file (`id_rsa`) you should have a public key located in `~/.ssh/id_rsa.pub`, it's time to setup the hosts file on your local machine.

Unix derivative systems keep the hosts file at `/etc/hosts`. This file is owned by root, so you'll need to use `sudo`.

    $ sudo vim /etc/hosts

Here is what a default hosts file might look like.

    ##
    # Host Database
    #
    # localhost is used to configure the loopback interface
    # when the system is booting.  Do not change this entry.
    ##
    127.0.0.1       localhost
    255.255.255.255 broadcasthost
    ::1             localhost
    fe80::1%lo0     localhost

Host entries are essentially local DNS overrides. It allows you to create a name and use that instead of the IP address for the server you just created.

I will continue on server names later, but the gist of it is naming your server makes it easier to remember it. As a bonus you don't need to memorize the IP address. Once IPv6 rolls out that will be a much bigger pain in the ass.

Append a line in the following format to your hosts file.

    [ip address] [chosen name]

For my server the ip address was 169.92.10.4[^1] and I wanted to call it `testbox`.

    169.92.10.4 testbox

Now test your connection.

    $ ping testbox
    PING testbox (169.92.10.4): 56 data bytes
    64 bytes from 169.92.10.4: icmp_seq=0 ttl=50 time=25.055 ms
    64 bytes from 169.92.10.4: icmp_seq=1 ttl=50 time=25.022 ms
    64 bytes from 169.92.10.4: icmp_seq=2 ttl=50 time=25.041 ms
    # ...

Enabling login via your ssh key is a quick step. First you need to get the public key onto the server. Short of a copy / paste, `scp` is the easiest way to do that. This will prompt you for your password.

    $ scp ~/.ssh/id_rsa.pub root@testbox:id_rsa.pub

Now we need to create a `.ssh` directory in the home folder, and copy the key into a new file called `authorized_keys`.

    $ ssh root@testbox
    root@testbox's password:
    Last login: Wed Nov 30 19:45:06 2011
    root@testbox:~$ mkdir .ssh && mv id_rsa.pub .ssh/authorized_keys
    root@testbox:~$ exit

Now that the keyfile is properly in place you can go ahead and re-try the login.

    $ ssh root@testbox
    Last login: Wed Nov 30 19:45:06 2011
    root@testbox:~$

It should drop right in, without prompting you for a password.

### Troubleshooting

Some common issues are presented below:

1. **Unknown host when running ping / ssh.** Try closing and re-opening the terminal. Sometimes the host file doesn't reload.
2. **Host still asks for a password.** Verify that you have correctly placed the keyfile. It should be in `~/.ssh/authorized_keys`.

***

That wraps up getting basic communication between your computer and the server. Here is what I'm planning on writing as a series overview:

1. [Basic server prep][part1]
2. [Setting up a user account / sudoers permissions][part2]
3. Introducing aptitude / package management
4. Setting up Apache
5. Setting up PHP and MySQL
6. Adding additional sites to apache
7. Useful Apache modules
8. Python, Ruby, and Node.js

[^1]: This IP address isn't actually valid.

[rackspace]: http://www.rackspace.com/cloud/cloud_hosting_products/servers/
[part1]: http://joshuakehn.com/2011/11/30/Setting-Up-a-Server-Part-1.html
[part2]: http://joshuakehn.com/2011/12/13/Server-Setup-Part-2-User-Accounts.html