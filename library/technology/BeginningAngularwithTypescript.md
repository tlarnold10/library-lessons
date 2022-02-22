# Beginning Angular with Typescript
__By: Greg Lim__
## Lessons Learned: 
- Interpolation in angular is the using of a variable inside html with double curly braces <h1>{{ title }}</h1>
- We can apply a async pipe in our ngFor to display a list from a database. Because data in the database arrive asynchronously the async pipe subscribes to the the table and returns the latest value emitted. They async pipe marks the component to be checked for changes
- We use CanActivate to control if a user is allowed to navigate to a path, where certain pages are allowed only to logged in users or users with certain permissions or role. We use CanDeactivate to display a confirmation box to the user and ask if they really want to navigate away for a page
- We can use square brackets to signify property binding
- Our components should not make http calls directly, but rather delegate that role to services
- For angular to connect to a backend server, we need Observables which is a concept introduced in a library called reactive extensions
- If a component, directive, or pipe belongs to a module in the imports array, don’t declare it in the declarations array. If you wrote a component and it should belong to this module, do declare it in the declarations.
- Template driven forms are easier to implement and involve writing less code. But they give us limited control over validation. Model driven forms have more code, but we have full control over validation.
- To format data in angular, we use pipes. For example, {{ data.releasedDate | date }} this is similar to Django and asp.net
- Properties marked as input or output will be visible from outside and available for property or even binding. If we want to do something like <rating [rating]=“4”></rating> to display a rating of 4 stars, we have to declare our component property with the @Input decorator. Inside the component we use ‘@Input() rating =0’. Think of this like setting a value of a component property from another component.
- Providers array contain the dependencies
- Dependency injection supplies instances of your classes that you depend on
- Components should only contain logic related to the view. Logic to get data from a server should not be in a component but instead be encapsulated in a separate class called a service
- @component function takes 2 attributes, selector and template. Selector property tells angular to display the component inside a custom <product> tag in index.html. Template specifies the html in-line that will be inserted into the DOM when the components view is rendered
- There are 4 main building blocks for angular app: modules, components, directives and services.