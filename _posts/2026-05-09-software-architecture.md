# Software Architecture

### Topics Covered

- [Modular Monolith](#modular-monolith)
- [C4 Model](#c4-model)

## Modular Monolith

While exploring which software architecture best suited the functional and non-functional requirements of a project I was working on, the first option that came to mind was a microservice architecture.  
However, while trying to validate that decision, I came across Martin Fowler’s article [*Monolith First*](https://martinfowler.com/bliki/MonolithFirst.html).

In this article, Fowler describes the challenges of starting a project when the domain boundaries are not yet well defined, and how a modular monolith can help address that uncertainty.  
It allows you to build strong internal boundaries and still lays the foundation to migrate to microservices later — if and when there’s a real need.

That perspective made a lot of sense to me. So, I decided to follow his suggestion and design a modular monolith architecture for my project.


### Concept

A modular monolith is an approach where the entire application lives within a single deployable unit, but its internal structure is organized into well-defined modules.  
Each module represents a specific area of responsibility, with clear boundaries and limited knowledge of other modules. 
This way, the system remains simple to build and deploy like a monolith, while still encouraging modularity and separation of concerns.  
It’s a middle ground between the simplicity of a monolith and the distributed complexity of microservices.


### Insights

I was working on a project where the functional and non-functional requirements were still vague, with many open questions about features and priorities.  
Our team was small, and there were no immediate plans to expand.  
We also wanted to reduce time to market by delivering a minimal but usable product and iterating from there.

Given these constraints, a modular monolith was a natural fit.  
It encouraged me to think early about:
- which modules to implement and their boundaries,  
- how modules should communicate and what their interfaces should expose,
- what databases and schemas should exist and their relationship with the modules.

At the same time, it provided a safety net — if we got those boundaries wrong, refactoring would still be manageable because everything lived in one codebase.  
We also avoided the operational overhead of microservices: asynchronous communication, network latency, deployment pipelines, and service discovery.

Another advantage was team collaboration.  
Even though we were all working in the same codebase, the modular structure allowed us to split responsibilities cleanly.  
Each developer could focus on a specific component, with confidence that changes wouldn’t ripple across the entire system — as long as module interfaces remained stable.

### Reflection

I’m still figuring out where modularity ends and over-engineering begins.  
Data management, in particular, remains a complex challenge — trying to establish a proper relationship between modules and databases without introducing unnecessary duplication is something I’m still experimenting with.

---

## C4 Model

When trying to document software architecture decisions, I often felt that traditional diagrams were either too detailed or too time-consuming.
I would spend more time styling diagrams than actually thinking about architecture.
In the end, I was never happy with the result. Some diagrams made sense only to developers, while others tried to capture everything at once and ended up confusing.

While researching for better approaches, I came across some talks about the  [*C4 Model*](https://c4model.com/) done by Simon Brown, which seemed like a good solution to my problems.


### Concept

The C4 Model defines four hierarchical levels of architectural views:

1. Context Diagram – shows how the system fits into its environment (users, external systems, dependencies).  
2. Container Diagram – shows the main applications or services that make up the system and how they communicate.  
3. Component Diagram – breaks down each container into its main internal components and their relationships.  
4. Code (optional) – dives into the implementation details, often represented as class or module diagrams.

Together, these levels create a consistent way to describe systems that can be understood by both technical and non-technical stakeholders.  


### Insights

The C4 Model provided a clear, four-layer structure that guides you from the big picture down to smaller details.
For someone like me, with limited experience in software architecture, having these guidelines was extremely helpful. 
They forced me to focus on one question at a time without getting overwhelmed by open questions or possibilities.


### Tools

To implement the C4 diagrams, I used [Structurizr Lite](https://docs.structurizr.com/lite), a local version of Structurizr.
It allowed me to render interactive diagrams directly on my machine without requiring cloud access, which was convenient for experimenting and iterating quickly.
The diagrams are recorded in a DSL file that can be easily shared with the team.

---
