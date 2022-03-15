---
layout: post
title: How Companies can serve their global clients faster by 60% using AWS Global Accelerator Service 
---

Tech

We are in a place where speed of the web services is no longer a want but a need! So, I thought to write my first tech blog about the same as I learned about the service in detail very recently.

Disclaimer: This blog would be useful if you're using AWS already for your global presence

# Introduction

The problem in hand is explained in detail in the below diagram, where the request from the client's browser or any kindof request(HTTP or TCP) from client's location takes these many turns to reach the AWS EC2 instances. 

![Normal Packet Flow]({{ site.baseurl }}/images/global_accelerator/intro.png)

# Explanation

To give you an example, Let's say you don't know the directions to reach a particular destination(Ofcourse without Maps). People at the station asks you to go x kms to reach the next station and ask there for the next station till you reach the destination. It's crazy, right. But, that's how the above method exactly works. This is how almost all your web resources are getting served. And, This problem is solved by AWS Global Acclerator Service by putting only a single station in between your Local ISP and the AWS Region.

# But, How did AWS manage to pull off this?

The Important part of the service is Anycast and it's communication between AWS Edge Locations.

About Anycast:

> Anycast is a network addressing and routing method in which incoming requests can be routed to a variety of different locations or “nodes.” In the context of a CDN, Anycast typically routes incoming traffic to the nearest data center with the capacity to process the request efficiently.

AWS with it's mammoth of resources, deployed Anycast setup in almost all the geographies, which is a very expensive and cannot be easily setup by any other company. Anycast routes the traffic to the nearest AWS Edge Location, which acts as a proxy for transferring the packets then it routes the request to the AWS Global Accelerator, which evaluates the distance, health and weight of the request and depending on that it will route the request to the apt Endpoint Group, which based on the healthchecks and the policies that you select will send the incoming requests to approriate endpoint. Now, all the client's IP will be pointing to the AWS Global Accelerator's IP.

![AWS Global Accelerator]({{ site.baseurl }}/images/global_accelerator/global_accelerator.png)

# Interesting Points to note

- A Global Accelerator can proxy n number of endpoint groups, each group associated to an AWS Region, where the requests are sent based on the geography. For example, If an user makes a request from India and we have an Endpoint at ap-south-1(Mumbai, India), then this endpoint will be called.
- You can test the service in realtime by sending packet size of your choice and see the results from here: [AWS Global Accelerator Speed Test](https://speedtest.globalaccelerator.aws/#/)


Thanks for reading and please provide your comments below

