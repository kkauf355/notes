# ASP.NET Core
A cross-platform, high-performance, open-source framework for building modern, cloud-enabled, Internet-connected apps.

## Models
The API interface
### Data Transfer Objects
DTO is an object that defines how the data will be sent over the network. (API users)

### Inversion of Control
IoC delegates the function of selecting a concrete implementation type for a class's dependencies to an external component.

### Dependency Injection
A specialization of the Inversion of Control pattern which uses an object - the container - to initialize objects and provide the required dependencies to the object.

#### Service registration types
Transient	(mail service)
Scoped		(repositories)
Singleton	(dataStore, FileExtensionContentTypeProvider)

## Entities
The database interface
### Entity Framework Core
Object-Relational Mapping (ORM) is a technique that lets you query and manipulate data from a database using an object-oriented paradigm

## Repository Pattern
An abstraction that reduces complexity and aims to make the code, safe for the repository implementation, presistence ignorant.

### Persistence Ignorant
Switching out the persistence technology is not the main purpose. Choosing the best one for each repository method is.
