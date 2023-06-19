---
layout: post
title: Where it all began
date: 2023-06-18
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: hmi-siemens.jpg#
fig-caption: # Add figcaption (optional)
tags: [hmi, integer overflow, variable speed drive]
---

It was in the middle of 2016 and i was doing some minor adjustments with a coleague of mine. The conveyors were running slowly and we needed to up the speed a bit. Next thing we notice is the product is falling on the floor, at an abnornally high speeds and flowing in the wrong direction.

## What have we done?
I quickly put back previous values back into the HMI and the conveyors ran in the correct direction at a slow pace again. Initial problem still persists, production cannot run in the current configuration. I was baffled and exited at the same time. I am an electrician at the time with no plant automation training at all and I knew I was going to breakdown the problem into small pieces without the use of Siemens and SEW Eurodrive proprietary software.

## Problem breakdown
I knew it was not a mechanical or electrical problem. I needed to focus on the application in the HMI(Siemens screen) and the variable speed drive. When you input values above a certain point in the allowable value range on the HMI, the conveyors run at speeds way beyond the value range of the limits set in the HMI and at opposite direction. Luckily for me I had studied digital electronics and I could tell that the variable speed drive is operating as it should when it is given negative values. Where does it get negative values from as I as not typing in negative values on the HMI?In the vsd, the integer value exceeded the expected integer value range in the microcontroller and in turn overflowed. In the microcontroller, they were valid values and were well within the limits of the vsd. 

## The solution
The most cost effective solution at the time without the involvement of the OEM was to edit the code in the microcontroller and change speed limits variable data type from short to an unsigned short as the operation does not need the conveyors to run in reverse. I was excited I found the problem and came up with the solution but I was disappointed that I was not the one editing the code. From then on and looking around, I saw a lot of software and in all sorts of gadgets. I knew I wanted to know more.
