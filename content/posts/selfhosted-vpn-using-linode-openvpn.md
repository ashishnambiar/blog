+++
title = 'OpenVPN + Linode = Selfhosted VPN'
date = 2024-03-31T14:25:24+05:30
draft = false
tags = ['journal', 'vpn']
+++

Creating a selfhosted VPN is actually quite easy, at least with linode (not
sponsored). I will try to summarize how I selfhosted a VPN, and the problems I
faced.

## Server Setup

I used a [Linode Video](https://www.youtube.com/watch?v=HPKgzup2fco) to get started. I will go skim through the steps regardless.

- click on "Create a Linode" (or something, I forgot)
- From the marketplace select OpenVPN
- Fill in necessary fields
- Choose the OS and type of server you want, I chose a Nanode(the cheapest one).

Once the Linode is created and initialized, the openVPN Access Server can be
accessed using the ip address of the created VM. In the browser you have type

`https://YOUR_LINODE_IP:943/admin`

This is to connect to the OpenVPN server as
admin.
This link will not open in a "incognito"/"private" tab.

Here I faced my first problem. I found out the admin OpenVPN Access Server
username is different from the one I entered during the creation of the Server,
and openVPN doesn't even ask for your password. The default username is
"openvpn" and the password is in your server. Ssh into your server by copying
the "SSH Access" link.

Now since you have access to your server on the terminal, you have to find the
`stackscript.log` file on the server. I simply did 

`cat /var/log/stackscript.log  | grep -i password`
> NOTE: for older versions of openvpn, you just do 
>
>`passwd openvpn` 
>
>to change
> the password. I am not sure if this works on the latest versions.

This might be different for you depending on the OS, I have the Ubutu 22.04 LTS.

Once logged in as admin, you have to go to "User Management" > "User
Permissions" and add a new user. This is for the user to connect to this
openVPN server. Set a username and password, with all other default settings.

**The server setup is complete at this point.** Next we just have to setup the
clients.

Now you can type 

`https://YOUR_LINODE_IP:943/?src=connect`

to go to user login, this is different from admin login. Use the username and
password created to login. These are a bunch of options for the clients
depending on OS.

## Setting up the client

This part is important for using the VPN on your devices. I will only cover
linux (Linux Mint) and Android here because these are the ones I have setup.

#### Android

First Install the application for OpenVPN; either "OpenVPN Access" or "OpenVPN
for android". OpenVPN mentions "OpenVPN for android" as the application for
"Advanced" users, The setup is simple for both.

From the user login in your browser download the "Connection Profile" just
below the OS options given. Once you have the `.ovpn` Connection Profile file
on your phone just click it. It will call an intent for the app you have
installed, just click the OpenVPN app and add the profile. I have tried this on
2 phones with 2 different apps, and it worked without much hassle.

#### Linux

For Linux Mint you can use the `openvpn` CLI tool. Similar to the android
setup. You need the "Connection Profile" file from the user login. 
- For "auto-login" Use 

`openvpn --config YOUR_CONNECTION_PROFILE.ovpn`

- For "user-locked" Use 

`openvpn --config YOUR_CONNECTION_PROFILE.ovpn --auth-user-pass`

There is [further
setup](https://openvpn.net/vpn-server-resources/connecting-to-access-server-with-linux/)
in linux for setting up the whole thing. But, with this you can start using
your vpn on your system.

It would be preferrable to have `openvpn3` which is mentioned in the setup.
But, I was unable to have it setup in my "Linux Mint Ulyana" Laptop. I might
update this part if I figure something out.

That's all.

---
---
As you might have noticed I am using Linode to create a selfhosted VPN. This is
because as soon as I hosted this blog on Digital Ocean, I tried to Login to
Linode. It seems they don't have a habit of sending
confirmation/acknowledgement emails or anything. But, I didn't get the free
credits for some reason. So, It didn't matter where I hosted this blog.

Anyways I want to make the blogs better with some images and gifs. I also want
to change the theme for this blog, because currently it is super bland and
basic looking. I used the default theme provided by hugo. This might change
in few weeks.
