---
layout: post
title: "Google Summer Of Code Report"
date: 2016-08-23 8:00:00
categories: jekyll Update
---

### Project - [Actionable Notifications Module](https://docs.google.com/document/d/1RIC_PevVgzE2LTzb5qLSaVXJmRKv9P4R8RkqQX_DdRs/edit?usp=sharing)

### Organisation - [Mifos Initiative](http://mifos.org/)

### Introduction

For the last two and a half months I have been working on building a notification module for the MifosX platform. This module will help the developers of the organisation to integrate notifications with their functionality with use of a simple API. For example, if a developer wants that whenever an event X occurs, a set of users must be notified about it. So with the use of this module it would become easy for the developers to notify other users without writing much code and need not worry about it's implementation.

### Overview of the project

My project mainly consisted of two parts, first one required working on the back-end code and the second part required working on the front-end code.

#### Generate and store the notifications (Back-end part)

- I have used pub-sub model to generate and receive the notifications.
- An external queue has also been used with the help of [ActiveMq](http://activemq.apache.org/) library to make the publication(generation) and subscription(reception) of messages to be asynchronous. Read the below given points to know why we are using an external queue.

 > **Advantages of using an external queue**

1. After inserting a message into an external queue it is not really required to process the message at the same time. It can be processed later i.e an external queue decouples the producer from the consumer.

2. The producer and consumer do not need to interact at the same time.

3.  An external queue will keep the processes in the application separated and independent of each other. So if one process that is processing messages from the queue fails, other messages can still be added to the queue and be processed when the system has recovered.

#### Deliver the notifications to the user (Front-End part)

- To deliver the notifications to the user on client side, the most common way is to poll the server after specific period of time to check whether the notifications for the current user are available or not. This is not very efficient technique to fetch notifications.

- The method which I have used to for the delivery of notifications is that, for every rest request which the UI makes there will be a response header 'X-Notification-Refresh' which will come along with the response and that header will contain the information like true or false. If that response header is true then fetch the notifications as there are unread notifications for the current user else ignore.

This pretty much sums up the short overview of my project. For detailed information about my project, navigate to the links given below.

### Links to the work done

1. [Notification Module Design](https://mifosforge.jira.com/wiki/pages/viewpage.action?pageId=133070890)
2. [Notification API Developer User Guide](https://mifosforge.jira.com/wiki/display/MDZ/Notification+API+Developer+User+Guide)
3. [Configure Notifications-End User guide](https://mifosforge.jira.com/wiki/display/docs/Configure+Notifications)
4. [Pull Request](https://github.com/apache/incubator-fineract/pull/178)
5. [Live Demo](https://www.dropbox.com/s/hefwvnvnziegatd/final.mp4?dl=0)

I would like  to thank [Edward Cable](https://www.linkedin.com/in/edcable) (Director of community programs, Mifos Initiative) for being so phenomenal during the entire period of Google Summer Of Code.


> **A big thanks to my mentor ([Pranjal Goswami](https://www.linkedin.com/in/goswamipranjal)) who always cleared my doubts even if he was too busy with his work :) and without whom it would have been very difficult to complete this project.**














