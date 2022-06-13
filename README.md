# Domain Driven Design

## Monolithic Architecture

- Modular
- Huge code bases
- Tight coupling between components
- Teams are composed of multiple smaller teams organized by technology and business
- Changes require coordination between teams
- Spans across multiple business functions

## Microservices Architecture

Arranges an application as a collection of _loosely couple services_. In a microservices architecture, services
are fine-grained and the protocols are light-weight.

MSA helps the business change at a faster pace. In other words, **MSA enables transformation**.

## Business Transformation

Business Transformation is an umbrella term that is used for referring to fundamental changes in how an organization conducts its business.

Example:

- **Microsoft** - from packaged software to subscription model
- **Amazon** - from an online book store to a marketplace
- **Apple** - from computers to iPod, iPhones, iPad, Music Store etc

### Why do businesses transform?

- **Environmental changes** e.g. new regulations
- **Competitive pressure** e.g. rapid rollout of new products
- **New opportunities** e.g. innovative technology
- **Customer demands** e.g. expects immediate response

## Digital Transformation

Digital Transformation is the process of using digital technologies to

1. meet the needs of **transformed business processes**
2. create innovative customer engagement mechanisms

> Digital Transformation supports the Business Transformation initiatives.

**Examples:**

- **Target** - a retail store in the US, till 2011 their website and fulfillment was outsourced to Amazon.
               In 2011, Target decided to transform their business. They invested heavily in digital technologies
               to integrate their supply chain inventories across the partner network, stores and their warehouses,
               and that enabled them to create new customer experiences.

- **Capital One** - used to be a traditional physical bank, but today it is a truly digital bank which has
                    no data centres of their own. They depend on AWS cloud for all of their technology needs.

- **Amazon** - uses multiple digital technologies to support their business transformation. Tech like AI/ML, API, Analytics etc
               are commonly used.

## Continuos Transformation

**Transformation is not a one-time initiative.**

> Continuos change + Adoption of digital technologies

- Businesses need to change on a continuous basis
- Rapid changes are needed in systems and applications
- Organizations need to keep up pace with new and evolving technologies

## A Business Perspective of Microservices

Microservices are self-contained units built to **realize a specific business capability**.

### Microservice Ownership

- Each service is build and operated by a small team
  - Teams are cross-functional and supported by domain expert
  - Two-Pizza teams : Team size ~8
  - _"We try to create teams that are no longer than can be fed by two pizzas; we call that the two-pizza team rule"_ - Jeff Bezos
  - **Better collaboration among smaller teams**
    - Frequent Software Releases
    - Faster response to changes in business
    - Tech becomes a competitive edge

### Why are Microservices organized around business capabilities?

- Each service can evolve independently
- Services are easily replaceable
  - No impact on other services if contracts are not changing
- Makes it easier for IT teams to understand the business
  - They don't need to dive deep into ALL business capabilities
- Higher alignment with business priorities
  - If ms1 is not undergoing frequent changes then the team may decide a release cycle of 2 weeks
  - Whereas if ms2 is undergoing some serious transformations then the team can decide a release cycle of every day
  - No time spent on managing conflicting priorities

### Critical Success Factor

To get the most benefit out of MSA, the teams need to carve out the appropriate business scope of Microservices to stay independent.

If NOT done correctly
- teams will be inter-dependent
- loss of advantage of MSA

This is where **Domain Driven Design** comes into picture!
DDD **bounded-context** is a representation of the business code for the Microservice.

## A Technical Perspective of Microservices

- **Loosely coupled set of services**
  - only external interfaces are known to consumer services
  - interactions are over the network or via async messaging
  - no code level dependencies
- Services interact over network
- Light-weight protocol like HTTP
- Independent code bases | deployments
- Decentralized governance
- Each service has a well-defined business scope

## What is Domain-Driven Design?

Is it possible to create complex banking software without good domain knowledge? No way. Never.
Who knows banking? The software architect? No. He just uses the bank to keep his money safe and available when he needs them.
The software analyst? Not really. He knows to analyze a given topic, when he is given all the necessary ingredients.
The developer? Forget it.
Who then? The bankers, of course.
The banking system is very well understood by the people inside, by their specialists.
They know all the details, all the catches, all the possible issues, all the rules.
This is where we should always start: the **domain**.

**How can we make the software fit harmoniously with the domain?**
The best way to do it is to make software a reflection of the domain.
Software needs to incorporate the core concepts and elements of the domain, and to precisely realize the relationships between them.
Software has to model the domain.

Somebody without knowledge of banking should be able to learn a lot just by reading the code in a domain model. This is essential.
Software which does not have its roots planted deeply into the domain will not react well to changes over time.

## Layered Architecture

<img width="50%" alt="Layered Architecture" src="https://user-images.githubusercontent.com/48696735/173322429-b3b167f9-f0ce-4775-b584-92349c272ebb.png">


### User Interface (or Presentation Layer)

Responsible for showing information to the user and interpreting the user's commands.
The external actor might sometimes be another computer system rather than a human user.

### Application Layer

Defines the jobs the software is supposed to do and directs the expressive domain objects to work out problems.
The tasks this layer is responsible for are meaningful to the business or necessary for interaction with the application layers of other systems.
This layer is kept thin. It does not contain business rules or knowledge, but only coordinates tasks and delegates work to collaborations of domain objects in the next layer down.
It does not have state reflecting the business situation, but it can have state that reflects the progress of a task for the user or the program.

### Domain Layer (or Model Layer)

Responsible for representing concepts of the business, information about the business situation, and business rules. State that reflects the business situation is controlled and used here, even though the technical details of storing it are delegated to the infrastructure.
This layer is the heart of business software.

### Infrastructure Layer

Provides generic technical capabilities that support the higher layers: message sending for the application, persistence for the domain, drawing widgets for the UI, and so on.
The infrastructure layer may also support the pattern of interactions between the four layers through an architectural framework.
