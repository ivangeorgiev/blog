---
title: "Why Do We Need A Data Platform"
date: 2019-04-08
last_updated: 2019-04-08 10:12AM CET
typora-root-url: ..\
---

Last updated: {{ page.last_updated }}

Some overview on the Enterprise Data Platform was given in the previous post [What is a data platform]({{ site.baseurl }}{% post_url 2019-04-06-what-is-data-platform %})?

## Benefits Summary

- Defining a Data Platform for the enterprise is what Urban Design is for the modern society - prepares the wild landscape, gives certainty, stability and predictability so that creative datapreneurs could build high-quality solutions with predictive cost.
- Data Platform is agile
  - Capabilities are added to the system incrementally, on-demand and by significance/priority.
  - Out-of-date technologies are easily upgraded or replaced.
  - The system easily scales out to fulfil solution needs.
- Data platform focuses on the architecture, thus taking care of the quality attributes (-ilities) of the system, running your solutions.
- Standardization and reusability through conventions, best practices, reusable components and solution blueprints.
- Improves / Enables data governance and data stewardship through reducing/eliminating custom execution logic and utilizing DevOps pipelines.
- Solutions portability across service providers - cloud: AWS, Azure, GCP etc. on-premise or hybrid.
- Template driven workflow generation reduces time-to-market and associated implementation effort.
- Automated deployment, monitoring and self-healing improve SLAs and lowers operations costs.
- Separation of business logic and execution logic allows for involvement of people with strong business knowledge into the solution process.
- Answers important questions before building solution:
  - What is the capacity of the system, running my solution?
  - How I could scale my solutions?
  - How I would extend the solution to fulfil new requirements?
  - What would be the cost of the solution?
  - How I could solve typical, industry-specific problems?

## Data Platform Miss-Understanding

- Organizations *Need to Build* Data Platform
  - This statement implies that organizations need to build some asset. The Data Platform (Foundation) is Architectural artefact. It is not built. It is designed. Platform components are created/instantiated from the platform when needed by a particular solution. Created components can than be reused in different contexts.
  - There is no associated capital investment in *"building"*. It is more like cultural approach, similar to the urban design - of thinking about the bigger picture before jumping into solution.
  - Enterprise Data Platform could be also a vendor data platform as Hortonworks (HDP), Cloudera (CDH), running on infrastructure as a service (IaaS). In this case there is a need of integration effort to turn it to platform as a service (PaaS):
    `IaaS + Vendor Data Platform = PaaS`
    - To make complete Enterprise Data Platform solution blueprints (reference architecture) must be added.
  - Organization builds a system which runs one or more solution. To build the system various components from the Data Platform are instantiated through integration of pre-existing (e.g. third party) components or implementing component interface as defined by the Data Platform.
- The Data Platform has a Business Case
  - There is no business case behind the Data Platform. As there is no business case behind the urban design. At least there is no explicit, immediate business case.
  - The difference between having a data platform defined and not having it is in what data solutions will look like, how easy it will be to add new solutions, combine and grow/extend existing solutions, maintain and keep updated the solutions and the whole technology stack.



## Data Platform Benefits Brainstorming

* Do not reinvent the bicycle!

* Do not repeat yourself - use a data platform!

* The digital economy has already arrived and will expand - Data Platform is a digital transformation enabler.

* Capable of ingesting, transforming and analyzing data from any variety (structured, semi-structured, unstructured - images, audio files etc.), velocity (batch or stream) and volume.

* Data Platform is the foundational framework which data intensive applications are built on - well designed platform results in better solution quality.

* Data Platform (Foundation) defines services and architectural blueprints necessary to approach common business problem scenarios thus making sure data solutions are feasible, cost effective and could grow to extend the solution.

* Data Platform is like Lego blocks design - a set of blocks (services) which fit and collaborate so that they could be used to build virtually everything.

* Having a Data Platform enables capacity planning.

* Using reusable processing components, packaged in a data platform enables end-to-end platform governance and data stewardship.

* The data platform takes care about the - scalability, security, performance, maintainability, portability and other -ilities of the IT solution. 

* Data platform brings standardization across the solutions, reduces the number and variety of the technologies and implements reusable components. This results in simple, easier and faster to implement and maintain solutions, requiring less engineering effort and skills.

* Data platform enables serverless, Function-as-a-Service (FaaS) architecture approach for any data intensive IT solution - in the cloud, hybrid or on-premise.

* To enable engineering of flexible and agile data intensive IT solution and at the same time, in parallel, the implementation of the underlying framework services and infrastructure, a Data Platform abstraction is used.

* Data platform defines interface between the IT solution and vendor specific data management application, utilities and frameworks, thus reducing the coupling and dependency on the specific vendors versions which in turn improves maintainability and upgradeability of solutions across the enterprise.

* Data solution without platform is like a building without architecture. Enterprise without data platform is like city without urban design.

  ![houses-in-hole]({{ site.baseurl }}/assets/blog/houses-collapse-in-hole.jpg){: width="500px" }

* The Data Platform lays the architectural foundation for IT solutions. Are you so rich to afford yourself building a solution without an architecture?

  ![Flooded living room in India]({{ site.baseurl }}/assets/blog/flooded-living-room-india.jpg){: width="500px" }



## === Work in Ideation ====

## Who Should be Interested?

Data Platform is not a business solution, it is an IT solution which provides capabilities as services to other IT solutions.

## When Should I Bother About Having a Data Platform?

If you ... (intention, need) ... than you ... (solution approach)...

