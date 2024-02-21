---
layout: post
title:  "Blog Week Three"
date:   2024-01-22 10:10:02 +0000
categories: blog posts
---
Welcome to our third blog entry for the development of Saving Animals by Josh and Jakub.

`Jakub`

During our third week, I proposed the Idea of using dock rising our project to make it deployable anywhere, to get rid of dependencies on our machines and to add complexity to our Project, it is also a great excuse to learn Docker and master it as both Josh and I struggled with it greatly during our DevOps module. Needless to say, Josh was on board too.

Firstly I did a whole bunch of research into how docker operates with its `Dockerfile` and `docker-compose.yml`. I quickly learned that I could build all of our apps in Docker on the same internal network in different containers with dependencies handled separately.

I started by putting our Django Rest API into a container alongside Postgres with PostGIS, I managed to find a lot of material online for it. A slim buster image of Python would be ideal due to its small size but the most recent one is still quite outdated so I decided to use slim-bullseye, PostGIS has its image which made the Database setup a lot easier.

Env variables played a huge role in this setup as they allowed both myself and Josh to log into the database automatically on each container saving us a whole lot of time. We have our Database credentials in a .env file which is read to Django with the python environment library. This allows us to configure our Django settings with preset variables that only we have access to as the .env file isn't tracked by Docker.

It took a great deal of research to set the two Docker containers up but it turned out great as Django even updated itself with each change just like on a `normal` machine. One Issue I ran into is with tracking the Database volume which is necessary for our data to save somewhere, as when it is first created even though the API is dependent on it, it tries to connect before the DB is ready resulting in an error. This can be resolved by just restarting the Api container.

