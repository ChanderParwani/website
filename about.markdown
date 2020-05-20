---
layout: page
title: About
permalink: /about/
---

## My little portion of the internet

Nothing particularly groundbreaking here, just a space for me to write about what I'm doing and a way for me to document what I know and what I'm learning. A motley aggregation of work-related learning, personal interest projects and other hobbies I have in my life.

## How this site works

This site is hosted as a static site on AWS S3. I use Route 53 for my domain hosting. The site is first created as a collection of markdown files which I have posted on [Github](https://github.com/s-k-hassan/website). Each post or alteration is posted as a new commit to the repo. At the moment I then manually trigger a Jekyll build to pull the repo down, build it and then push it up to S3. A plan for the future is to be able to automate this aspect of the process, but for now where there are several updates that can happen in short succession it is easier to do it all manually.
