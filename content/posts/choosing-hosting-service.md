+++
title = 'Choosing Hosting Service'
date = 2024-03-30T15:15:02+05:30
draft = false
tags = ['journal']
+++

## Finalizing choice for hosting service

I finally decided to use Digital Ocean's "App Platform" to host this blog site.
So this is currently available on both github pages and DO.

This is just a small update to keep you in [The
Loop](https://open.spotify.com/track/4E8SsodyGGLgv7HPeSisw5?si=1a093a5fb6a445d7).
Anyways, I feel like I got this out of my chest so now I can start writing some
more meaningful blogs that might be more relevant to coding and stuff. I am
going to be posting here kind of semi-randomly, without sticking to any
specific topic, but it will most probably about coding. I will try to put a
blog either weekly or bi-weekly.

## The Digital Ocean Setup

It was actually quite easy. Since I already had the whole thing already setup,
all I had to do was host it using DO. But there was a small issue.

For some reason, when creating a new thing with "App Platform", I got the Error
`No Components Detected`. This was because DO didn't detect the hugo project
like it says in the
[tutorial](https://www.digitalocean.com/community/tutorials/how-to-build-and-deploy-a-hugo-site-to-digitalocean-app-platform#step-4-deploying-to-digitalocean-with-app-platform).
`DO` needs an `index.html` to detect that the project is a static site.
Thankfully, you can just remove the `public` directory from the `.gitignore`,
so that you can set the "Source Directory" from DO. It was slightly silly, but
it wasn't a big issue.

I know that this is not Linode, and not Object Store, that [I
wanted](/posts/hugo-blog-setup) . I initially considered using Digital Ocean's
"Spaces Object Store", but I thought, it is better to have something than to
mess with something I have never done before. I might try it later if a
necessity comes, I may directly shift to Linode once that is available to me.

## Next Step

I want to get a domain; possibly for free, so that I can have something to
simply give to people without
[`ondigitalocean`](https://blog-evibj.ondigitalocean.app/) in the domain. Looks
kind of unprofessional.
