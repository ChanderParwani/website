---
layout: post
title: "Playing with Playbooks"
date: 2020-05-21 14:00:00 +1000
categories: 100daystooffload homelab technology ansible
---
One of the better aspects of being stuck in lockdown is having the opportunity to be able to explore new technologies that I've always wanted to experiment with but have never found the time or focus to dedicate to. The past few days I've been doing just that in the form of working with Ansible. While it's hardly a new technology and the time of configuration management being the latest technology du jour has since passed, it's a fundamental building block for DevOps/SRE methodologies and something I've wanted to explore. While going through the process of creating new virtual machines in my homelab for trying diferent things out I've been running through the process of creating everything manually during the initial install, then endeavouring to replicate the process through Ansible playbooks.

As of a couple of weeks ago, my go-to when starting up a new VM was to pull one of my installation scripts from GitHub and execute it to get everything I needed. This worked pretty well, I was mostly able to do everything that I was looking to do as part of this. The problem came after the installation, when I needed to do things like update packages or create small adjustments. Using a tool like Ansible actually made things a lot easier than I thought they would - it's not like I'm running hundreds (or even tens) of VM's - manually running each script isn't overly time consuming or complex. But it was nice to see everything neatly declared and helped me to visualise the logic I was running each time. I am by no means a Linux, DevOps or programming whiz, but it was simple enough to grasp how the YAML syntax worked. Give or take a few expletive filled moments regarding things like indentations or referencing commands that had been deprecated since the StackOverflow post I was reading had been answered.

## Break things down as much as possible

If a playbook goes wrong, it can be confusing trying to find out where it fell apart. Maybe someone with more experience can see it straight away but I certainly can't. For me the solution was to break down each individual step as much as possible to see exactly at which point a command got stuck. At least then I would have *some* context as to what I was looking at.

## Sometimes when it's successful, it isn't

Biggest pain in the arse. Playbook runs through and says everything is fine and configured. SSH into the host only to find that none of the changes have been applied. I ran into this for quite a while with the Gems module for Ansible. To be honest I still have no idea what I was doing wrong or how to fix it. I just went and used the Command module to call the necessary lines myself. Maybe in future I'll look at it again but I'm not going to go and invest any more time for the moment in trying to figure it out when I have a workaround that works and can be repeated without causing issues. Whenever you run a playbook, verify that what you see in theoutput from Ansible is what's actually happening

## Change one thing at a time

I made a change or several to a command I was running in a playbook, which naturally broke the command. Without knowing what the cause was I had to step through everything to see where possible issues were occuring. Much easier instead to make one change, test, confirm, repeat. If your playbooks are the holy-grail idempotent files that Ansible pushes us to aspire towards, running it over and over won't (shouldn't) cause any problems.

## Google is your friend. Posts from 2015 may or may not be

It's great learning a technology that everyone else has already learned, you have a whole internet of knowledge available from people who were once as clueless as you. However the answers that are marked as correct aren't always still correct. A perfect example of this is Ansible changing some of its terminology. So while you're scratching your head as to why `sudo: yes` is coming up as invalid, check that the product developers haven't updated the terminology since then to `become: yes`. It'll save you half an hour double- and triple-checking your indentations that you never had to do. Also, while the documentation for Ansible is by and large pretty good, there's some answers that you will undoubtedly overlook. Such as the difference between Autoremove and autoremove as options. Both do the same thing, but have different YAML syntaxes.

## Just do it

At first it seemed pretty overwhelming to give Ansible a go. For all the talk I'd heard about how easy it was to use and understand, it seemed like something that was difficult at best to comprehend if you weren't some Linux propeller-head. Turns out that's only half-true. While some of the more advanced capabilities are well beyond my reach, getting a basic set of playbooks running (without errors even!) wasn't too hard.
