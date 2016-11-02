---
layout: post
section-type: post
title: Using Chef to manage NetApp
category: code
tags: [ 'a-team', 'chef', 'devops', 'learning', 'netapp', 'tutorial']
---

<large>Why manage with Chef?</large>
Chef is a configuration management tool that helps operations maintain repeatable and consistent deployments of infrastructure. A lot of focus has been on deployment of servers and VM's through Hyper-V or VMware, but I think that doing infrastructure configuration management would include things like network and storage. Good news, NetApp has a cookbook for Chef! So, let us take a look at design and deploy.

<large>Designing for NetApp</large>

NetApp ONTAP software doesn't allow for the chef-client to install locally. NetApp is really opening up on the OS side, but due to security/performance reasons they don't yet allow third party installs such as this. So, how do we manage the array if the client isn't installed? Well, we will need a server that the client will install on and has access to both the Chef server and the NetApp array. 
