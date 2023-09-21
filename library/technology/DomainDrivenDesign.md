# Domain-Driven Design: Tackling Complexity in the Heart of Software
__By: Eric Evans__
## Lessons Learned:
- There are many advantages to understanding the business domain of the software. One of the best is the fact that you can effectively communicate with end users.
- Never forget that software exists to solve a problem for a user.
- Effective domain models are known as knowledge crunchers. They take a ton of data and distill it to the relevant/important bits. Creating a simple view from the mass amount of data.
- Diagrams and drawings with models, properties, and relationships are very important in creating the common domain design.
- Code, classes, methods, and modules should have the same naming scheme as if you were communicating with the end user.
- Talking through concepts out loud with users allows you to better build a common language and go through scenarios.
- __Unified Modeling Language (UML)__ is a diagram of models/objects/classes and their relationships to other models/objects/classes. They represent the skeletons of ideas. The model is not the diagram.
- Model should bind to the code design. Mapping should be obvious. Changes to design should change model and vice versa.  Code becomes and expression of the model.
- OOP works better with model driven development because the relationships and objects can be directly mapped to the domain common language. 
- You can isolate the domain model from the other bits of the application using a __LAYTERED Architecture__. This includes the following layers:
	1. User Interface
	2. Application
	3. Domain
	4. Infrastructure - common services
	- Layers are meant to be loosely coupled
	- An example of this architecture is MVC (Model View Controller)
- Entities correspond to an object that has a specific unique identifier. This can be different from an attribute. Because attributes can be changed, but an identity, that thing specifically, cannot be changed. 
- Value objects have no conceptual identity. Examples would be colors or the number 4. Often used as attributes of entitie4es. We don't care which instance of a value object we use.
- Services stand alone in the model. They don't track state like entities or value objects. Named as a verb, rather than a noun. Most concerned about what it can do. 
- Repository is used to access and query the database. The client can use the repository, that abstracts the technical needs of the database querying, and still maintain utilization of the domain model.
- When users or domain experts use words or phrases that are not in your model, that is a warning sign that you are likely missing something. 
	- Another red flag is when a portion of the domain model is extremely complex.
- Supple, or elegant and flexible, design is a complement to Deep Modelling. While deep modelling is about digging out domain concepts with the domain experts, and reflecting those concepts in code, Supple Design is about building that code in a way that is easy to understand, modify and extend, in sum: code that is maintainable.
- Keep in mind object constraints and build them into the object. For example, a bucket object could only hold so much water. Create a separate method to handle the constraint checking.
- Predicates are functions that evaluate to TRUE or FALSE.
- Name classes and operations to describe their effect and purpose. This relieves the client developer from needing to look into the class or operation. These names should tie back to the ubiquitous language so everyone can quickly identify its purposes.
- A side effect is any effect on the state of a system.
	- Operations that return results without side effects are functions.
	- Functions are lower risk than operations that change state/side effect produced.
- __Declarative programming__ is when you write code in such a way that it describes what you want to do, and not how you want to do it. An example would be SQL.
- You can use analysis patterns to help in the development of your domain model. They provide some key concepts so you have something to work off of. 
	- Definition: analysis patterns are groups of concepts that represent a common construction of business modeling. An example would be accounting model. 
- Classical refactoring scenario: 
	- A developer or two sitting at a keyboard, recognizing some code that can be improved and then changing it. Using unit tests to verify results.
- Refactor towards deep domain insights when:
	- The design does not express the team's understanding of the domain.
	- Important concepts are implicit in the design (and you see a way to make them explicit)
	- You see an opportunity to make some important part of the design suppler.
- Context: in terms of models, every model has a context. The context may be a certain part of the code, or the work of a particular team. For models created during a brainstorming session, the context would be the content of that session.
- __Extreme Programming (XP)__ is a good fit for maintaining a coherent design that is being changed by multiple people. However, continuous integration is a vital piece of this. 
- When working with other systems that do not use the same model, you can create an isolating layer between the two in order to provide clients with functionality in terms of their own domain model. This requires little to no changes to either system as the isolating layer translates in both directions as necessary between the two models. 
- The __core domain__ is the part of the model that is distinctive and central to the purpose of the application. This is where most value should be added in your system's domain model.
- The core domain is high risk because it is often unexpectedly difficult, and the project cannot succeed without it.
	- Your best devs should be dedicated to the core domain. Others, including contractors or off the shelf solutions, can tackle generic subdomains. 
- Six essentials for strategic design decision making:
	1. Decisions must reach the entire team.
	2. The decision process must utilize feedback.
	3. The plan must allow for evolution.
	4. Architecture teams must not take all the star developers. 
	5. Strategic design requires minimalism and humility. 
		- Keep It Simple Stupid.
		- Do not over engineer a solution
	6. Objects are specialists, developers are generalists