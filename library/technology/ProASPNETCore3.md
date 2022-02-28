# Pro ASP.NET Core 3
__By: Adam Freeman__
## Lessons Learned:
- A Repository pattern is a design pattern that mediates data from and to the Domain and Data Access Layers ( like Entity Framework Core / Dapper). Repositories are classes that hide the logics required to store or retrieve data. Thus, our application will not care about what kind of ORM we are using, as everything related to the ORM is handled within a repository layer. This allows you to have a cleaner separation of concerns. Repository pattern is one of the heavily used Design Patterns to build cleaner solutions.
- Using the IQueryable<T> interface allows us to ask the database for just the objects that we require using standard LINQ statements. Without it, we would have to retrieve all of the objects from the database and then discard the ones we don't want, which is an expensive operation.
- IQueryable<T> is typically used instead of IEnumerable<T> in database repository interfaces and classes.
- Dependency injection allows the HomeController object to access the application's repository through the IStoreRepository interface without knowing which implementation class has been configured.
- View model class, used specifically to pass data between a controller and a view
- Tag helpers use IUrlHelpFactory objects to generate urls that target different parts of the application
- Creating an object in the models folder is one way to create a form
- Unit test follows a pattern called arrange, act, assert. Arrange refers to setting up the conditions for the test, act refers to performing the test, and assert refers to verifying that the result was the one that was expected
- The Fact attribute is applied to each method to indicate that it is a test
- Unit testing is a form of testing in which individual components are isolated from the rest of the application
- The null conditional operator is a single question mark. This makes coding for situations with nulls, much easier to manage
- LINQ helps you filter your model results
- When returning a view object you can pass the arguments of the view name and the model
- Model binding is what allows the HttpPost attribute to connect what model object data is passed to the server. Incoming data is parsed and the key/value pairs in the HTTP request are used to populate properties of domain model types
- Use tag helpers to dynamically generate urls, ids, and names. This is much better than hard coding it yourself
- The razor view engine will use the name of the action method when looking for a view file
- Model is often referred to as the domain model
- Each page in the controller is known as an action, so index() is the action you are taking for that page. Each public method defined by a controller is an action, which means you can invoke the action method to handle an HTTP request
- Entity framework is the object-relational mapping (orm) framework, which represents data as .net objects.
- Test-Driven Development (TDD), the core idea is that you write the tests for a feature before implementing the feature itself
- Entity Framework Core provides access to the database through a context class
- So an interface is kind of like an abstract class with nothing but abstract methods, and since there are no methods with actual code, there is no need for any fields. Properties are allowed though, as well as indexers and events. You can consider an interface as a contract - a class that implements it is required to implement all of the methods and properties.
- Coalesce in C# is ??