---
title: Announcing Fluvio Cloud Platform
author: 
    name: "The Fluvio Team"
description: Today we are pleased to announce the Fluvio Cloud, a fully managed installation of Fluvio open source.
metadata: NEWS
date: 2021-01-10
slug: announcing-fluvio-cloud-platform
url: /blog/2021/01/announcing-fluvio-cloud-platform
img: blog/images/fluvio-cloud/social/cloud.jpg
tile: blog/images/fluvio-cloud/social/cloud-tile.svg
twitter-card: summary_large_image
hidden: true
---

Today we are pleased to announce the Fluvio Cloud, a fully managed installation of Fluvio open source. Fluvio Cloud is now in alpha and you can sign up using the link below:

<center><a class="btn btn-primary" href="/signup" role="button">Sign Up for Fluvio Cloud</a></center>

Fluvio is a high performance distributed data streaming platform for connected Apps. While interacting with Fluvio is simple, managing the infrastructure is not. Fluvio Cloud is is a fully managed data streaming solution maintained by the Fluvio creators. No infrastructure required, just sign up for an account and use the product with the same CLI as Fluvio open source.

## Our Mission

Our mission with Fluvio is to make building real-time applications easy. We believe that modern business requires real-time interaction, analysis, and adaptation. Yet, the challenge that many groups are facing is that building real-time infrastructure is a painful, expensive, and error-prone endeavor. We set out to solve this challenge by creating a general-purpose real-time application platform, backed by the fastest and safest data streaming engine possible.

Today many applications are built using persistence patterns that effectively undermine the ability to perform real-time operations. These applications use classic databases and data lakes that utilize a write-first-then-query paradigm, an anti-pattern for real-time application. Real-time applications need to process data as soon as it hits your network, then write the results for safekeeping.

Integrate Batch processing as a 2nd anti-pattern ??

## Introducing Fluvio 

Fluvio is a high performance distributed platform that coordinates all real-time data exchanges in an organization. It deploys in minutes, operates hands-free, and covers a broad range of use cases. The platform is suitable for services such as: 

* Log aggregation for servers
* Command center for IOT devices
* Middle tier for microservices
* Notification services for mobile devices
* Fully-featured collaborative apps, with chat, voice, video, geo-tracking, and more.

The Fluvio data platform for real-time collaboration was built on these three pillars:

1. [Data Streams](#data-streams)
2. [Collaboration](#collaboration)
3. [Ease of Use](#ease-of-use)

### Data Streams

Streaming Data is data that is generated and delivered continuously. A data stream often consists of individual messages that describe events that have occurred. A key advantage of streaming data, as opposed to having batches of data delivered periodically, is that the average time to take action on an event is much lower. Since streaming data is delivered immediately, events can be processed and acted upon immediately. Therefore, a critical prerequisite to building real-time collaborative applications is having a scalable, durable, low-latency data streaming platform. We built Fluvio to meet this need.

Fluvio data streaming platform is built to optimize the following: speed, scale, retention, and resilience.

#### Speed

Fluvio takes advantage of all system cores and hardware IO interfaces to achieve high-speed and low latency. This is a game-changer for businesses like financial services, gaming and augmented reality companies, or service providers offering 5G services.


#### Scale

As organizations grow and new services are deployed, the volume of real-time data grows in proportion. Growing organizations must be able to effectively scale their data streams and platforms. Fluvio is designed for parallelism and horizontal scale. 

At the core Fluvio’s design are Streaming Processing Units (SPUs). A Fluvio cluster can handle hundreds of SPUs and each SPU can serve thousands of consumers. This makes the platform capable of handling any real-time data streaming needs, from a small one-person prototype to the most demanding multi-team, multi-app, globally distributed environments.

Fluvio allows you to scale-up your cluster gradually rather than provisioning for peak. As your demand for real-time streaming grows, you can simply add SPUs and Fluvio will do the rest. 

Horizontal scale ensures you don’t need new real-time infrastructure to deploy new services. You also won’t need to ask your IT department to work overtime when you roll out a marketing campaign that brings more clients to your service.


#### Retention

The term retention is often found in the context of storage systems, where it defines the time period the data should persist for. Organizations may have data retention policies that range from 5 to 10 years. In the context of real-time data systems, retention periods are more often measured in seconds to minutes.

Fluvio extends the retention period for real-time data streams from seconds to years. Each data stream is an immutable store, where the messages are written in the order they are received. A long lived immutable store sets the foundation for a series of new features. The data streams can become the authoritative data source (A.K.A. <a href="https://en.wikipedia.org/wiki/System_of_record" target="_blank">System of Record (SOR)</a>) for all events generated by different systems organization-wide. These events can be played back anytime in the future. Playbacks can be used to:

* Recover a persistent store
* Rebuild an in-memory database
* Playback historical data for new features
* Perform retrospective analysis
* Run audit reports, and more. 

For example, suppose a dealership stored all appointments in a database that was corrupted during a power outage. The last backup was performed the previous week and 7 days of data had been lost. Since Fluvio was used, the database changes were also captured as events in a data stream. The events were played back and all appointments were recovered.

The translation of database operation into events is also referred to as [Change Data Capture (CDC)](/tutorials/rust/mysql-cdc/). For additional information, check out our Fluvio CDC tutorial.

#### Resiliency

Resiliency is the ability to continue operating in the event of a failure. A platform responsible for real-time data services must be highly resilient. 

Fluvio data streams are replicated for durability and they can survive multiple points of failure. Failures may result from system crashes, network outages, or reasons yet to be determined Should a failure happen, Fluvio ensures that data streams remain available with minimal interruption. Once a failure is detected, the cluster redistributes workloads and temporarily removes the failed component from the quorum. Upon recovery, the cluster ensures the component is fully synchronized before it is allowed to re-join the quorum. For additional information on high availability, check out the [Fluvio architecture](https://fluvio.io/docs/architecture).

Fluvio supports a wide range of deployment scenarios: single cloud, multi-cloud, cloud-to-data center, and more. If Fluvio is deployed in a single availability zone, it protects against server outages. When deployed across availability zones, Fluvio protects against zone outages, and when deployed in hybrid mode it protects against data center outages. It’s up to the users to define the deployment model most suitable for their environment.

###### To sum up:

* Fluvio is low-latency. 
* Fluvio also allows you to scale up and manage data streams as your needs increase. 
* Fluvio’s retention reliably stores incoming data streams for years. 
* Fluvio’s resiliency provides protection against outages and crashes.


### Collaboration

At the top-most level, a real-time collaboration app has 3 components: a collaboration interface, a real-time streaming platform, and one or more business logic services. 

The collaboration interface allows users to communicate with each other and produce an action. The real-time streaming platform passes the action to one or more services, and returns a result. The services translate the request into a response, based on the organization’s business logic.

#### Collaboration Interface

The design of the collaboration interface depends on the organization's needs. Some organizations prefer to integrate with purpose-built communication tools such as Slack or Teams. Others prefer to build custom interfaces where they can control the workflow end-to-end. Fluvio supports both of these collaboration styles.

In terms of support for purpose built tools, Fluvio gives access to a programmable interface that allows the creation of a custom connector. Connectors can be configured to produce actions, listen for responses, then publish the result. For organizations that prefer to roll-out their own collaboration interface, Fluvio’s programmable interface can serve as a single point of contact for the application to send and receive events. Fluvio has several sample programs:

* [Chat App](/tutorials/node/simple-chat/)
* [Bot Assistant](/tutorials/node/bot-assistant/) 

to give developers a framework for their first collaboration app. 

#### Real Time Streaming Platform

A powerful use-case for a real-time data streaming platform is to connect services that typically operate independently, enabling cross-service capabilities. Fluvio offers language-native programmable interfaces that each service can utilize to send or receive messages, to and from real-time data streams.

In the dealership example there are multiple services that need to communicate with each other :

* Advisors: coordinate customer communication. 
* Services: look-up maintenance schedules and assign mechanics.
* Billing: charges customer credit cards and generates receipts.

Fluvio handles multi-service communication through data streams called `topics`. When a service completes work, it generates an event that is published to a `topic`. Fluvio receives the event and notifies all other interested services. Consuming services receive notification, complete their work and generate an event on their own, and so on. Let’s look at an example:

1. When a customer arrives at the dealership, advisory service looks-up the car and publishes an event on the `advisory` topic. 
2. Services receives the event, schedules mechanics to perform the work, and generates an event on the `services` topic.
3. Billing receives the event, charges the customer credit card and sends an event with the amount paid on `billing` topic.

#### Business Logic Services

When organizations roll out their own real-time collaborative apps, they implicitly build services to implement the business logic.

Fluvio programmable interfaces are built for polyglot applications, where developers have the freedom to use their preferred programming languages to implement a service. Fluvio develops and maintains language native APIs for Rust, Node and Swift. Upcoming releases will roll-out additional native language APIs for Java, Python, Go, and common languages.

###### To sum up:

* Fluvio supports both purpose-built and custom collaboration tools, letting users of both choose how to receive and manage events.
* Fluvio’s streaming platform lets independent services communicate through data streams/topics.
* Fluvio supports the creation of business logic services in common programming languages. 


### Ease of Use

Fluvio ensures ease of use by making its core components easy and intuitive to utilize. Fluvio is an open-source distributed system with two core components: the cluster running streaming services and the clients that communicate with the cluster. The clusters are available in two flavors: Fluvio Cloud and Fluvio Open Source. They are managed by Fluvio clients through the CLI or programmatic APIs.

Beyond the core components, Fluvio prioritizes operational efficiency through declarative configuration management and reconciliation. The declarative approach lets developers simply declare the goal of their configuration and then the configuration management tool will do the rest. Meanwhile reconciliation ensures any cluster changes are still in line with the stated goal of the system.   

#### Clusters

##### Fluvio Cloud

[Fluvio Cloud](/docs/fluvio-cloud/) eliminates the need to install and operate a cluster. The installation, upgrading, and all other maintenance tasks are managed by our team. 

##### Fluvio Open Source

[Fluvio Open Source](https://github.com/infinyon/fluvio) can be installed in private data centers, public clouds, or on personal machines. [Fluvio CLI](/docs/cli) has built-in pre-check tests and installation scripts for most common environments. To install Fluvio, first download the Fluvio CLI from Github, and then run the installer. 

#### Clients

##### Fluvio CLI

[Fluvio CLI](/docs/cli) covers a broad range of operations: cluster installation, data stream provisioning, produce/consume operations, and more. Checkout the CLI Guide for a detailed list of commands.

Fluvio CLI has built-in multi-cluster support, where the CLI can switch from one environment to another with one command. This feature is particularly useful when testing client software against different data sets. Developers can build the code against a local data set, then switch to a cloud instance to run the code against production data

#### Programmatic APIs

Fluvio has programmatic APIs and role-based access for all operations. The operations are divided in two groups: admin and user. Operations such as cluster installation and topic management are reserved for administrators, whereas producer/consumer are open to users.

API interfaces are currently available in Node, Rust and Swift, while other languages will be implemented in upcoming releases. Check out [Fluvio docs](/docs) for the API references.

#### Operational Efficiency

Fluvio uses declarative configuration management to simplify manageability and improve operational efficiency. With declarative configuration, the operator specifies the intended outcome, rather than how to accomplish it. For example, a topic with 3 partitions is a desired outcome. Given this outcome, Fluvio automatically distributes the topics across the SPUs to achieve optimal performance and reliability.

Anytime there are changes in the cluster, Fluvio uses reconciliation to ensure all outcomes can still be met. This allows the system to self-heal and recover from any conditions automatically without human intervention. For example an SPU loses power and it disconnects from the cluster in the middle of receiving a batch of records. A few minutes later, the SPU comes back online and the reconciliation loop kicks-in.  During reconciliation, the SPU is brought back in sync with the cluster before it resumes its operations.

###### To sum up:

* Fluvio clusters can be either cloud-based and automatically managed by the Fluvio team, or open-source.
* Fluvio clients allow management of the clusters with either the Fluvio CLI or a programmatic API.
* Fluvio ensures operational efficiency with declarative configuration management and reconciliation, making cluster management both intuitive and reliable.


## Conclusion

Modern business is happening in real-time. Customers demand immediate results, and business leaders require operational insight approaching clairvoyance. The transition from collaboration to real-time collaboration requires a foundation that can provide the data for the business context in real-time. This transition doesn’t need to be difficult.

Fluvio is the first purpose-built platform for real-time collaboration. With Fluvio, the focus is on business data. We bring context first, then apply collaboration features to enable real-time decisions. Our product is in early infancy and we look forward to working with you, the community, in providing us feedback as we iterate through the next wave of collaborative features.

Join us, create an account in our [Fluvio Cloud](https://cloud.fluvio.io), check out our open source project in [Github](https://github.com/infinyon/fluvio) or connect with us in [Discord](https://discordapp.com/invite/bBG2dTz).

We look forward to talking to you, see you soon.


== Others

Today many applications are built using a three-tier paradigm, and use persistence patterns that effectively undermine the ability to perform real-time operations. 