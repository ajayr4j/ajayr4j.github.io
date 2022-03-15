---
layout: post
title: SaaS Metrics to look in a Startup/Company
---

SaaS

A company can become successfull only if many factors align like people, culture, product, customer success, sales, etc., unless some company shoots up due to some magical USP. But, For an investor or someone who is evaluating company all the above factors are kindof intangible for them. So, I'm adding here all the metrics an investor/evaluator will look at. **Metrics** is something that will bring out the truth about any company, afterall math won't let you down. If you're looking to join, invest or buy a company this would definitely come in handy. All the informations is gathered from Medium, Youtube, etc.,

# Some Abbrevations:

| Short | Expansion                                           |
|-------|--------|
| LTV   | Customer Lifetime Value                             |
| Churn | Move out of the company(Dollar, Customer, Employee) |
| CV    | Customer value                                      |
| ACL   | Average customer lifespan                           |
| APF   | Average purchase frequency                          |
| APV   | Average purchase value                              |
| CRO   | Conversion rate optimization                        |
| ARR   | Annual Recurring Revenue                            |
| CAC   | Cusomter acquisition cost                           |


# Some Formulae :bear:

- CAC = Total marketing and sales expenses($) / Total number of new customers acquired
  - Expenses that are covered for marketing and sales: Ad Spend, Employee Salaries, Creative Costs, Technical Costs, Publishing Costs, Production Costs and Maintaiing Inventory
- APV = Divide total revenue / Number of purchases 
- APF = Number of purchases / Number of unique customers
- CV = APV x APF
- ACL = Number of years a customer continues purchasing
- LTV = CV x ACL
- Net new ARR = New ARR + Existing ARR - Churned ARR

*Ideally all the above calculations are made for the course of a year*

# Some Pattern :chart_with_upwards_trend:

All the below points are analysed over the period of 20 years, designed as a guess or method to make a conclusive statement about the company's health. So, there are always very niche market that won't fit in this. But, this should fit for the most case. Some cases that are below won't work for seed stage startups, but it's good to make these comparisions in a timeseries graph than making these calculations from a single point of time to see the trajectory more clearly.

- LTV:CAC = 3:1, Because if the LTV is as nearly as CAC(1:1) then it's a clear case of burning out or a slow exit if it's 2:1 and if the ratio is 5:1, then there is an oppurtunity to invest more in CAC as the company might loose out potential customers if not done.
- Churn rate per month should be less than 20%
- Customer Success:
  - Negative Churn = Revenue from existing customers > Revenue lost from churning customers
  - Analyise customer feedback, tickets related to them 
- Cusomer Churn vs Dollar Churn:
  - This metric should be analysed, invest sales and marketing resources into the type of client that brings in good amount of money, than 

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
