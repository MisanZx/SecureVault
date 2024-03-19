# Pfsense

## What is Pfsense?

pfSense is a firewall/router computer software distribution based on FreeBSD. The open source pfSense Community Edition and pfSense Plus is installed on a physical computer or a virtual machine to make a dedicated firewall/router for a network.

Below I will share with you setting up and configuring some basic settings to get you started. This technology request is dedicated to a good work colleague of mine that is interested in a bit of networking and is in his your years within IT, hoping this proves useful for him and others.



## Setting up Pfsense

You can install Pfsense on any compatible hardware, please check the vendor site for the systems supported. For my examples I will showcase how to set this up on vmware workstation.

[https://www.vmware.com/products/workstation-player.html.html](https://www.vmware.com/products/workstation-player.html.html)

First head over to the webpage and download the iso image:



<figure><img src="../.gitbook/assets/image.png" alt="" width="375"><figcaption></figcaption></figure>

Todays' date of download the ISO is 16/03/2024 so your should be a newer version.

_always recommended to download the latest version from the vendors' website._



Extract the zip after fully downloaded and create a new virtual machine.

_When installing the OS, please ensure that enough allocated resources are applied to the device. My own recommendations are 4GB of RAM and 40GB of storage space. I have had strange issues with less resources on my virtual machine so your results may vary._

Depending how you are networking the device I would recommend connecting up the cables (virtually) to get it all ready for the setup.

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

I hit next to all of the default steps.

on this part hit the "space" bar to select the option.

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

hit "enter" to the next screen and it should start installing.

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

After when it is fully done the machine will reboot.

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Since we have already added the other VMnet on the setup, it should auto create the lan and assign it as em1 as shown above.

## Connecting to your GUI web interface

Setup another OS and connect it only to VMnet2 (lan), this will connect you to pfsense before connecting to anything outside of that network.

I have a windows machine I am using as the management console, lets call it MGT.

On the MGT machine, go to the lan ip address: 192.168.1.1.&#x20;

You should get something like this:

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

It is okay, this is normal, continue anyways.

Default login details:

Username: admin

Password: pfsense

_Highly recommended to change the default password to prevent people accessing your system if they are on your management machine or on your network._

_Going through the GUI, you can change any of the settings within the wizard as it gives nice example and descriptions, if unsure click "next" till you get to the end screen._

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>



Awesome, you have made it this far. You are now all setup so you can explore to find out what you want you want to do.&#x20;

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

## Some Ideas what you can do

You could add more machines to your network and restrict the services:

This is the default rules and there is hierarchy so make sure its in the right order.&#x20;

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

Some other ideas:

* You could limit the traffic limit from one place to another with routing limits
* Create aliases for common ports if you are adding always the same type of ports / addresses.
* Monitor traffic

Still need more documentation, please go to [https://docs.netgate.com/](https://docs.netgate.com/) to find out more.



