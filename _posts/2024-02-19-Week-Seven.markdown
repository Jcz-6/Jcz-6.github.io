---
layout: post
title:  "Blog Week Seven"
date:   2024-02-19 10:10:02 +0000
categories: blog posts
---
Welcome to our seventh blog entry for the development of Saving Animals by `Josh and Jakub`.

This is our final week for the project the pressure is on but we are on the right track. This week is all about the frontend and documentation for Saving Animals.

We have implemented a good chuck of the frontend pages by now, we also used navigator.geolocation to get the user's geo-cords through the front end which passes them to Flask. The `Vet Org and User` functionality is almost finished too but we ran into a couple of issues.

First of all the vet schedule models turned out to be bad, we spent a significant amount of time coming up with a solution that doesn't conflict with each other, and we narrowed down the issue to the report which needed to be attached to the schedule or org report but how if its not made yet? The answer: Make the user fill out a form which creates the report and attaches it to a schedule/org report in the backend automatically. With this innovation, we managed to display and update the pages accordingly.

Secondly the navigator.geolocation API turned out to be a huge disappointment as it doesn't serve HTTP requests anymore, we didn't know this as `localhost` is a `trusted source` and we were developing locally all this time, so when it came to testing it on a phone hotspot we were scratching our heads at why it doesn't work.
Luckily we found an IP Geolocation API which serves all requests but isn't as accurate, we quickly swapped the API calls and it works great.

Thirdly Redux mistakes were haunting us throughout due to the lack of error messages, minor spelling mistakes made the whole state not dispatch making it return undefined, on top of that the Serializers in Django were a pain since we did not know we had to set `depth` of the serialized data. This made the requests return only the object id's with no data.

Finally, we were having trouble displaying a background image on our landing page, even though we followed the documentation to a tee.

The documentation turned out to be a lot more pleasant than expected, this was most likely due to this being our project which we know inside out the only problem we ran into was finding ways of running tests for our project since it all in docker with quite long and heavy build times ruling out CD/CI for the most part and there just isn't that many ways of testing a frontend or sockets for example.

We also managed to put our project on Nginx successfully but we still haven't decided whether we will use white noise or Nginx to host our static files for our presentation.
