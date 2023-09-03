# Software Design

## Design Principles

Design principles are tools to manage complexity, giving us the freedom to compartmentalize our systems and allowing us to break our system into pieces so we can make changes in one place without affecting another.

We make readable code by moving ideas that are unrelated further apart (modularity) and moving related items closer together (cohesion).

Systems adhering to these principles are easier to understand, easier to test, easier to change and so easier to incrementally evolve into something better.

### Modularity

Breaking down a complex system into smaller, manageable modules or components. Each module should have a specific, well-defined purpose or responsibility. Promotes code reusability, maintainability, and ease of testing. By isolating functionality into modules, it becomes easier to understand, develop, and maintain different parts of the software independently. This approach also supports collaborative development, as team members can work on separate modules concurrently.

### Cohesion

The degree to which the elements within a module are related or share a common purpose. High cohesion means that the elements within a module are closely related and focused on a single task or responsibility, while low cohesion indicates that the elements may have diverse purposes and should be separated into different modules. Designing for high cohesion helps ensure that a module is focused, easy to understand, and less prone to bugs, as its functionality is well-defined and self-contained.

### Separation of Concerns

Dividing a software system into distinct sections, each addressing a different aspect or concern of the application. For example, you might separate user interface (UI) concerns from business logic, data storage, and communication with external services. This separation enhances code maintainability and flexibility, as changes to one concern do not ripple through the entire system. It also promotes reusability and simplifies testing of individual concerns.

### Loose Coupling

Reducing the dependencies between different modules or components in a system. When components are loosely coupled, they can operate independently and are less affected by changes in other parts of the system. This promotes flexibility and scalability, as you can replace or upgrade components without affecting the entire system. Loose coupling is often achieved through well-defined interfaces, dependency injection, and decoupling mechanisms like message-based communication.

### Abstraction and Information Hiding

Encapsulation of the details of a module's implementation and exposing only the necessary interfaces or abstractions to other modules or components. Abstraction allows you to work with high-level concepts and ignore implementation details, which simplifies code understanding and reduces the impact of changes. Information hiding involves concealing internal data and behavior, exposing only what is essential for interaction. This not only protects the integrity of a module but also allows for changes to be made internally without affecting other parts of the system.





