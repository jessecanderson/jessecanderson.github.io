---
layout: post
section-type: post
title: Can Veeam have DevOps?
category: Veeam
tags: [ 'veeam', 'devops' ]
---

Let us start with "What is Veeam"? I haven't had a chance to really talk much about backup and recovery solutions on here so people may not know what this product is.

Veeam Software enables the Always-On Enterprise by providing data center availability with high-speed recovery and data loss avoidance.

Why is this important? Veeam is one of the leading providers of recovery solutions in the world. They have in depth integrations into NetApp and VMware products and provide a solution that works easily and consistently. But Veeam has another feature, not really hidden but I don't think it is highlighted enough either. Veeam can take the data from your system and spin up <b>exact copies</b> of these systems for you to test and validate.

Think about that for a second....I will wait......

Good? What ideas came to mind. If you could have an exact copy of your production systems to test on, what would you do with it? Test your latest build? Validate any patch or updates to the OS maybe? Or just run:

<pre><code data-trim class="bash">
sudo rm -r /
</code></pre>

Because admit it, you always wanted to see what that would do to your system?

But seriously, in our new DevOps world of continuous deployments, testing, configurations management....even though we can spin up machines that "look" like our production environment...why would we not want the chance to test out their stuff on replicas of the production environment? Veeam actually gives us this ability through their virtual labs. The idea of tying this into your application pipeline is not all that far fetched. Veeam supports Powershell and REST api's so it should not be that difficult to come up with some scripts that you could then embed into your workflow and automate the deployment of the virtual lab, pushing out updates or new code to your application through continuous deployment or continuous integration products, and then validate through automated testing. Best of all, it's done on production replicas, not just systems that are configured "like" production.

This way we can stop throwing things from Dev over the wall to Ops.

![Ops Problem](https://qph.ec.quoracdn.net/main-qimg-463fa5d5d739f4c69e6a252429942ba5?convert_to_webp=true){:class="img-responsive"}

Over the next few blog posts, I'm going to layout the idea of integrating Veeam into your workflow and we will look at what it may take to automate the whole process using modern operations tools.
