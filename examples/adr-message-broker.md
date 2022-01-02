# Architecture Decision for API Gateway

Contents:

* [Summary](#summary)
  * [Issue](#issue)
  * [Decision](#decision)
  * [Status](#status)
* [Details](#details)
  * [Assumptions](#assumptions)
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


### Assumptions

The front-end applications are typical:

  * Typical users and interactions

  * Typical browsers and systems

  * Typical developments and deployments

The front-end applications is likely to evolve quickly:

  * We want to ensure fast easy developments, deployments, iterations, etc.

  * We value provability, such as type safety, and we are fine doing a bit more work to achieve it.

  * We do not need legacy compatibility.

The back-end applications are higher-than-typical:

  * Higher-than-typical goals for quality, especially provability, reliability, security, etc.

  * Higher-than-typical goals for near-real-time, i.e. we do not want pauses due to virtual machine garbage collection.

  * Higher-than-typical goals for functional programming, especially for parallelization, multi-core processing, and memory safety.

We accept lower compile-time speeds in favor of compile-time safety and runtime speeds.


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


We decided that VMs have a set of tradeoffs that we do not need right now, such as additional complexity that provides runtime capabilities.

We believe that our core decision is driven by two cross-cutting concerns:

  * For fastest runtime speed and tightest system access, we would choose JavaScript and C.

  * For close-to-fastest runtime speed and close-to-tightest system access, we choose TypeScript and Rust.

Honorable mentions go to the VM languages and web frameworks that we would choose if we wanted a VM lanauge:

  * Closure and Luminous

  * Java and Spring

  * Elixir and Phoenix


### Implications

Front-end developers will need to learn TypeScript. This is likely an easy learning curve if the developer's primary experience is using JavaScript.

Back-end developers will need to learn Rust. This is likely a moderate learning curve if the developer's primary experience is using  C/C++, and a hard learning curve if the developer's primary experience is using Java, Python, Ruby, or similar memory-managed languages. 

TypeScript and Rust are both relatively new. This means that many tools do not yet have documentation for these languages. For example, the devops pipeline will need to be set up for these languages, and so far, none of the devops tools that we are evaluating have default examples for these langauges.

Compile times for TypeScript and Rust are quite slow. Some of this may be due to the newness of the languages. We may want to look at how to mitigate slow compile times, such as by compile-on-demand, compile-concurrency, etc.

IDE support for these languages is not yet ubiquitous and not yet first-class. For example, JetBrains sells the PyCharm IDE for first-class support for Python, but does not sell and IDE with first-class support for Rust; instead, JetBrains can use a Rust plug-in that provides perhaps 80% of Rust language support vis a vis Python language support.


## Related


### Related decisions

We will aim toward ecosystem choices that align with these langauges.

For example, we want to choose an IDE that has good capabilties for these languages.

For example, for our front-end web framework, we are more-likley to decide on a framework that tends to aim toward TypeScript (e.g. Vue) than a framework that tends to aim toward plain JavaScript (e.g. React).


### Related requirements

Our entire toolchain must support these languages.


### Related artifacts

We expect we may export some secrets to environment variables.


### Related principles

Measure twice, build once. We are prioritizing some safety over some speed.

Runtime is more valuable than compile time. We are prioritizing customer usage over developer usage.


## Notes

Any notes here.
