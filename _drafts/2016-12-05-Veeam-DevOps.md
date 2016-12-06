---
layout: post
section-type: post
title: Can Veeam have DevOps?
category: Veeam
tags: [ 'veeam', 'devops' ]
---

Let us start with "What is Veeam"? I haven't had a chance to really talk much about backup and recovery solutions for infrastructure on here so people may not know what this product is.

<h2> Veeam Software enables the Always-On Enterprise by providing data center availability with high-speed recovery and data loss avoidance.</h2>

Why is this important? Veeam is one of the leading providers of recovery solutions in the world. They have in depth integrations into NetApp and VMware products and provide a solution that works easily and consistently. But Veeam has another feature, not really hidden but I don't think it is highlighted enough either. Veeam can take the data from your system and spin up <b>exact copies</b> of these systems for you to test and validate.

Think about that for a second....I will wait......

Good? What ideas came to mind. If you could have an exact copy of your production systems to test on, what would you do with it? Test your latest build? Validate any patch or updates to the OS maybe? Or just run:

<pre><code data-trim class="bash">
sudo rm -r /
</code></pre>

Because admit it, you always wanted to see what that would do to your system?

But seriously, in our new DevOps world of continuous deployments, testing, configurations management....even though we can spin up machines that "look" like our production environment...would would not want the chance to test out their stuff on replicas of the production environment? Here is where the real power comes into play. And the idea of tying this into your application pipeline is not all that far fetched. Veeam supports Powershell and REST api's so it would not be that difficult to come up with some scripts that you could then embed into a Chef cookbook or maybe a Jenkins workflow that would deploy your test environment for you. 
