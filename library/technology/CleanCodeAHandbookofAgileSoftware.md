# Clean Code: A Handbook of Agile Software
__By: Robert C Martin__
## Lessons Learned: 
- Functions should either do something or answer something. Either your function should change the state if an object, or it should return some information about that object
- The java language has the notion of synchronized, which protects and individual method. The synchronized keyword introduces a lock. All sections of code guarded by the same lock are guaranteed to have only one thread executing through them at any given time. Recommendation: Avoid using more than one method on a shared object
- A design is simple if it follows these rules: 1. Runs all the tests 2. Contains no duplication 3. Expresses the intent of the programmer 4. Minimizes the number of classes and methods
- We should be able to write a brief description of the class in about 25 words, without using the word if, and, or, but.  Singe Responsibility Principle (SRP) states that a class or module should have one, and only one, reason to change. Open-Closed Principle (OCP) classes should be open for extension but closed for modification
- The name of the class should describe what responsibilities it fulfills. If we cannot derive a concise name for a class, then it is likely to large.
- Clean tests follow five other rules that form the acronym FIRST. Fast, tests should be fast. Independent, tests should not depend on each other. Repeatable, tests should be repeatable in any environment. Self-validating, the tests should have a boolean output. Timely, the tests need to be written in a timely fashion, unit tests should be written just before the production code that makes them pass
- Three laws of TDD: first law, you may not write production code until you have written a failing unit test. Second law, you may not write more of a unit test than is sufficient to fail, and not complaining is failing. Third law, you may not write more production code than is sufficient to pass the currently failing test.
- When using third party code, try to write some test experiments to understand how the code works before you add it into your system
- Data transfer object, DTO, is a class with public variables and no functions. However, something more common is the “bean”, which have private variables manipulated by getters and setters
- Objects hide their data and expose their operations. The things that are hard for object oriented are easy for procedures (code using data structures), and the things that are hard for procedures are easy for OO.
- Don’t automatically create a get and set method for every variable. Think about what you’ll actually need
- Horizontal max characters should be between 80 to 120
- Variables should be declared as close to their usage as possible. Local variables should appear at the top of each function, because the function should be short
- In Java, file size is closely related to class size. So when you create a new file, the structure should be similar to a newspaper. The name should be simple but explanatory. The topmost parts of the source file should provide the high level concepts and algorithms. Detail should increase as we move downward, until at the end we find the lowest level functions.
- When you find yourself in a position where you need to write a comment, think it through and see whether there isn’t some way to express yourself in code. An acceptable use of a comment would be an explanation of intent, or the reason behind a decision
- Functions should do one thing. They should do it well. They should do it only
- The first rule of functions is that they should be small. The second rule of functions is they should be smaller than that
- Our goal is to make our code as easy as possible to understand. We want our code to be a quick skim, not an intense study
- Methods should have verb names like postPayment, deletePage, or save
- Class and objects should have noun or noun phrase names like Customer, Wikipage, Account, or AddressParser
- Single letter names can only be used as local variables inside short methods
- Use actual English words as much as possible
- The name of a variable, class, or function  should tell you why it exists, what is does, and how useful it is. The name should reveal its intent.
- The ratio of time spent reading vs writing code is well over 10:1
- Clean code is focused. Each function, class, modular exposed a single minded attitude that remains entirely undistracted, and unpopulated, by the surrounding details
- Bad code tempts the mess to grow. When others change bad code, they tend to make it worse
- The only way to make the deadline, the only way to go fast, is to keep the code as clean as possible