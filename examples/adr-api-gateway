# Architecture Decision for API Gateway

Contents:

* [Summary](#summary)
  * [Issue](#issue)
  * [Decision](#decision)
  * [Status](#status)
* [Details](#details)
  * [Constraints](#constraints)
  * [Positions](#positions)
  * [Argument](#argument)
  * [Implications](#implications)
* [Related](#related)
  * [Related decisions](#related-decisions)
  * [Related requirements](#related-requirements)
  * [Related artifacts](#related-artifacts)
  * [Related principles](#related-principles)
* [Notes](#notes)


## Summary


### Issue

As a technology team of Company X, we develop and manage business workflows with a monolith project. Since our team grows rapidly and the domain starts to be more complicated, we would like to migrate our systems to the microservices by seperating the domain.

As a first step, we should choose an open-source API Gateway because of technical requirements such as Authentication, Authorization. We have two major needs;

* The language of source code suitable for our development team in terms of know-how
* Open-source options.


### Decision

We decided to use **KrakenD** as API Gateway. Our motivations are as follows;

* KrakenD is open-source and has a large community.
* Our development team has hands-on experience with GoLang.
* Stateless Architecture
* Performance


### Status

Accepted on 2 Jan. 2022. We are open to new alternatives as they arise.


## Details

### Constraints

We have a couple of constraints as follows;

* Open-source development and community for less cost
* High throughput, low latency
* Performance issues
* Development team know-how


### Positions

We considered these API Gateways:

  * KrakenD

  * Ocelot

  * Kong

  * Tyk
  

### Argument

Summary per API Gateway:

  * KrakenD: open-souce, large community, stateless architecture, faster than Kong and Osilot, written by GoLang.

  * Kong: rejected. a bit complex, written by Lua, pricing for more features, harder to manage than KrakenD and Ocelot.

  * Ocelot: rejected. written by C#, great community, easier to use with .NET services.
  
  * Tyk: rejected. enterprise-ready open-source API gateway, AWS marketplace, pricing for cloud, GoLang support. 


We believe that our core decision is driven by two cross-cutting concerns:

  * For faster responses, lower request latency, we would choose KrakenD.

  * For microservices written by .NET framework, we would choose Ocelot.


### Implications

For Ocelot, Back-end developers will need to learn C#. This is likely an easy learning curve if the developer's primary experience is using C#.

For KrakenD, Back-end developers will need to learn GoLang. This is likely an easy learning curve if the developer's primary experience is using GoLang. The most of the team has hands-on experience with GoLang.

KrakenD is relatively new when compared to Ocelot. However, they have detailed documentation. Adaption of KrakenD will be easy.

The performance benchmark of KrakenD and Ocelotshows that KrakenD is better than Ocelot. In addition, we developed POCs for both KrakenD and Ocelot. The results again demonstrate that KrakenD has a greater performance than Ocelot.


## Notes

Any notes here.
