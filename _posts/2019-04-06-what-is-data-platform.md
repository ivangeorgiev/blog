---
title: "What is a Data Platform?"
date: 2019-04-06
links:
   - title: Big Data Platform
     url: https://www.techopedia.com/definition/29951/big-data-platform
draft:
   - "Big data platform is a type of IT solution that combines the features and capabilities of several big data application and utilities within a single solution. It is an enterprise class IT platform that enables organization in developing, deploying, operating and managing a big data infrastructure /environment."
   - "Big data platform generally consists of big data storage, servers, database, big data management, business intelligence and other big data management utilities. It also supports custom development, querying and integration with other systems. The primary benefit behind a big data platform is to reduce the complexity of multiple vendors/ solutions into a one cohesive solution. Big data platform are also delivered through cloud where the provider provides an all inclusive big data solutions and services. " 
---

## (Big) Data Platform Definition

(Big) Data Platform generally is Platform as a Service (PaaS) type of IT solution. It provides features and capabilities for big data storage, compute services, query, big data management, data governance, business intelligence, etc. It also supports custom development, querying and integration with other systems. The primary benefit behind a big data platform is to reduce the complexity of multiple vendors/ solutions into a one cohesive solution.

Enterprise Data Platform defines solution blueprints as guidelines for creating and implementing various solution scenarios using the (Big) Data Platform capabilities.

### Approaches towards (Big) Data Platform

Following the separation of concerns principle, logically coherent capabilities are provided by loosely coupled components, usually third party tools (services). The tools are combined so that they collaborate and make together a consistent Platform as a Service (PaaS). The Enterprise Data Platform could be described using following layers:

1. Core capabilities (Core platform) implemented as integrated set of third party components.
   1. Core platform is usually deployed using some form of templates (Ansible, Ambari Blueprints, Azure Resource Manager templates etc.)
2. Reusable platform components - mostly processing component which execute data transformations
   1. Reduce dependency on the tools from the Core Capabilities layer.
   2. Improve governance by reducing or completely removing solution-specific coding.
   3. Reduce solution implementation effort by removing duplication and minor variation of same functionality across solutions.
   4. Reduce "time-to-market" by enabling template-based workflow generation.
   5. Enables serverless architecture, providing Function-as-a-Service.
3. Solution Blueprints - example scenarios:
   1. Stream (Real-time) Processing 
   2. Automated Enterprise BI
   3. Real-time recommendation API

The most important part of the Big Data Platform approach is the Core Platform which is the base, fundamental layer. The selection and implementation of this layer determines the qualities of the solutions. There are different approaches towards the Core Platform.

1. ***Create Your Own Distribution***
   Select and integrate yourself tools from the ecosystem to build the Core Data Platform. This approach was very popular a couple of years ago with the Hadoop hype. The variety, complexity and short lifespan of the tools in the Hadoop ecosystem proved this approach to be very inefficient.
2. ***Integrate Vendor Core Data Platform***
   Some vendors specialize in creating consistent Core Data Platform. For example: Cloudera (CDH), Hortonworks (HDP), MapR, etc. Enterprise can integrate the vendor solution, turning it into PaaS. Although the popularity of this approach fades away with the wide adoption of cloud computing, it is still valid for on-premise solutions. Variations of the integration:
   1. Bare metal - traditional cluster. Not very flexible.
   2. Virtualization - Containers or Virtual Machines - private cloud.
3. ***Combine Cloud Services***
   Cloud services provide much better separation of concerns - storage, networking, data processing, scheduling, visualization, etc. At the same time components are designed to integrate well with each other. It makes it very easy to start quickly implementing a solution, focusing on the particular problem being solved.

Very often teams jump into solution implementation. Neglecting the need for the two layers (Reusable Components and Solution Blueprints) which complete the Enterprise Data Platform.

- Huge variety of frameworks, programming languages and implementation approaches
- Repeated algorithm implementations in common purpose programming languages, combined with metadata
- Implementation tightly coupled with specific tool selection and tool versions
- High complexity of implementation, requiring specific combination of technical and domain expertise at a very high level

See the follow-up post [Why Do We Need Data Platform]({{ site.baseurl }}{% post_url 2019-04-08-why-we-need-data-platform %}) for discussion on the reasons and importance of the Enterprise Data Platform.