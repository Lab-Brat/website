---
title: "GSoC 2023: Week 2"
date: 2023-06-04T09:21:52+03:00
tags:
    - opensource
    - gsoc
categories:
    - GSoC2023
ShowToc: true
---

This article is a summary of all the changes made on 
[Automated Gentoo System Updater](https://wiki.gentoo.org/wiki/Google_Summer_of_Code/2023/Ideas/Automated_Gentoo_system_updater) 
project during **week 2** of GSoC.  

Project is hosted on [Github](https://github.com/Lab-Brat/gentoo_update)  


### Progress on Week 2
This week all about packaging and testing. 
The updater is still in its infancy, but it's much better to 
package everything nicely right away and not think about this in the future.

I kicked things off by bundling all the code into one directory and set it up as a Python module. 
Then, with some automation magic I whipped up a Github Actions workflow that takes care of 
publishing the package to PyPI. The idea was to make it installable using pip.

But to my surprise it turns out Python pip had it's permissions in OS severely limited after some 
recent changes. To get the package to install on the system, it demands the ‘--break-system-packages’ 
flag. This doesn't look very user friendly 😅.

So, I took a different route and crafted an 
[ebuild](https://github.com/Lab-Brat/gentoo_update_ebuild) instead, 
which I've shipped off to the GURU 
[repository](https://github.com/gentoo/guru/tree/master/app-admin/gentoo_update). 
It's already merged to the main branch and is available for installation on Gentoo!  

Apart from packaging I also penned some unit tests for the main Python file 
and did more testing in Docker containers and VMs.

### Challenges

### Plans for Week 3
The updater's output currently is too messy and it's all over the place. Time to tidy that up!
An important part of the project is the parser that will read and understand logs from emerge. 
I plan to start coding the parser next week.

And I can't forget – I need to learn how to post blogs on Gentoo's website.