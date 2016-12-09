---
layout: post
section-type: post
title: Can Veeam have DevOps? (Virtual Labs)
category: Veeam
tags: [ 'veeam', 'devops', 'code' ]
---

Lets start with our Veeam and DevOps discussion by looking at how we can configure and utilize Veeam to make a replica of our production environment.

The idea behind the virtual labs is to validate any of the backups and replicas that Veeam is currently protecting. It does this by deploying a proxy appliance into your VMware infrastructure that will isolate the virtual lab networking environment. Then Veeam will recreate your environment behind this proxy appliance, including a mirror of all networking configuration.

An added benefit of this design is it gives you a sandbox environment to play in also. These virtual labs are temporary recreations from a specific point in time backup and all changes are sent to the redo logs on a specified datastore, so when your done testing it all goes away with no impact to production systems. 
