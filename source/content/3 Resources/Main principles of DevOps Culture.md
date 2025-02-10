---
created: 20230926-1524
tags:
  - Resources/devops
  - Resources/talk
---

The four main principles are:

#### Colaboration and comunication

The idea is to break the walls and make specialized teams communicate openly. It comes from a time where Operations teams and Development teams worked separately and with different objectives in mind, so their vision of the others and of the product as a whole was always partial.
Nowdays this extends to every kind of team like QA, Stakeholders and such.

> We are trying to make developers and testers to speak live, not via complex decadent systems.

#### Shared Responsibility

> This **doesn't** imply getting devs to learn how to configure a server.

Every party should be responsible for the success or failure of the product. Devs are expected to oversee the product through the entire pipeline; a dev who understands testing and operation challenges is more likely to simplify deployment and maintenance through code. When operations understands the system's business goals, they can work with devs in defining operational needs of the system more clearly.

#### Business-oriented Mindset

The basis of the devops mindset is the specific mindset of bringing *value* to the customer. In practice this means stopping the thoughts of "I'm making code that should pass some quality gate to meet an abstract goal" and replacing it with "This features will be great for the end user"

#### AUTOMATION

Learning from mistakes and automating repetitive tasks leaves much more time for communication and creative work. This should mean going beyond just automation of tests and deployments; one can automate many parts of the product processes like monitoring, bug reporting and failure recovery.


From "Establishing SRE Foundations: A Step-by-Step Guide to Introducing Site Reliability Engineering in Software Delivery Organization"
> Now that you know what DevOps is, let’s explore it in more detail. This will be useful when
> comparing DevOps with the methodologies just described.
> DevOps defines five pillars of success.15
> 1. Reduce organizational silos.
> 2. Accept failure as normal.
> 3. Implement gradual changes.
> 4. Leverage tooling and automation.
> 5. Measure everything.

