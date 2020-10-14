---
title: Requirements
weight: 5
pre: '<b>a. </b>'
chapter: false
---

{{% notice note %}}
This is just a subset of some of the main features to knock out an initial system design.
{{% /notice %}}

So what are our requirements for our backend.

- A mobile friendly API to handle user interaction. For the moment this can be limited to

  - Opening the app and seeing a list of places in a mile radious along with their current queue times
  - The ability to virtually join a queue while not physically there
  - Check-in to a venue when you join a queue
  - Automatically update the wait time once you've entered the venue
  - Receive Notications when you're at or near the top of the queue

- A queing system which matches a bar to a user

- A Reporting API which can pull aggregated metrics for venues and users on things like

  - Wait times
  - How busy places are
  - Peak times

  An initial API spec can be found on [Apiary](https://yurtyme.docs.apiary.io/)
