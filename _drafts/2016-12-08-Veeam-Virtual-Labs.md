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

To deploy this, you can either use the GUI (which works great but isn't as stream lined) or use some PS scripts that will deploy the environment to the selected datastore.

To do this, you will need to make sure the Veeam PowerShell commands have been installed on the local Veeam server or on the remote server. I will be testing on the local Veeam server.

Let us start with a host to run this on. We will grab a host with the following command:

<pre><code data-trim class="Powershell">
$host = Get-VBRServer -Type ESXi -Name "nameOfServer"
</code></pre>

This will reach out to the VBR server and grab the ESXi Host with the name "nameOfServer". Here, we don't really have to specify a name for the host we want to deploy this to, but just in case you do then you can.

Next we will select the datastore to dump our redo logs to:

<pre><code data-trim class="Powershell">
$datastore = Find-VBRVIDatastore -Name "nameOfDatastore" -Server $host
</code></pre>

Here we are selecting the redo logs specific datastore named "nameOfDatastore" from the server "nameOfServer" that we assigned to the variable $host. This makes sure we are on the specific host and don't accidentally grab a datastore from somewhere else.

Finally, let us tie these two things together and create our virtual lab:

<pre><code data-trim class="PowerShell">
Add-VSBVirtualLab -Name "myAwesomeVirtualLab -Server $host -Datastore $datastore
</code></pre>

Here is where we actually create the virtual lab using the host we specified earlier as well as the datastore for redo logs.
