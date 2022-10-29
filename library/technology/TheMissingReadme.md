# The Missing README: A guide for the New Software Engineer
__By: Chris Riccomini and Dmitriy Ryaboy__
## Lessons Learned:
- Advise you to document conventions, onboarding procedures, and other oral traditions on your team. You will get a lot of comments and corrections. Do not take the comments personally. The point is not to write a perfect document but rather to write enough to trigger a discussion that fleshes out the details. This is a variation of Cunningham’s law, which states that “the best way to get the right answer on the internet is not to ask a question; it’s to post the wrong answer.”
- Run experiments to learn how code truly works.
    - Debuggers are your best friend when experimenting. You can use them to pause running code and see running threads, stack traces, and variable values. Attach a debugger, trigger an event, and step through the code to see how the code processes the event. Although debuggers are powerful, sometimes the easiest way to understand a behavior is a few well-placed log lines or print statements.
- Read high-quality open source code, particularly libraries you use. Don’t read code front to back like a novel: use your IDE to navigate through the codebase. Diagram control flow and states for key operations. Dig into the code’s data structures and algorithms. Pay attention to edge case handling.
- Pending work is tracked in tickets or issues. Read through team tickets to see what everyone is working on and what is coming up. The backlog is a good place to find newbie tickets, too.
- Don’t choose a project based on what you think you need to learn. Find problems you are interested in solving, and solve those problems using the tools you want to learn. A goal that intrinsically motivates you will keep you engaged longer, and you’ll learn more.
- Asking questions effectively will help you learn quickly without irritating others. Use these three steps: do research, ask clear questions, and time your questions appropriately.
- Try to find the answer yourself. Even if your colleagues know the answer, put in the effort—you’ll learn more. If you don’t find the answer, your research will still be your starting point when you ask for help.
- Keep track of where you looked, what you did, why you did it, what happened, and what you learned.
- Once you reach the end of your timebox, ask for help. Only exceed the timebox if you are making good progress. If you go past your first timebox, set another. If you are still not sure of the answer after the second timebox, cut your losses and ask for help. Stopping takes discipline and practice—hold yourself accountable.
- Describe what you know when asking a question. Don’t just share your raw notes. Outline what you’ve tried and discovered succinctly.
- Post questions so that multiple people can respond (multicast) at their own pace (asynchronous). Do this in a way that’s visible to everyone so it’s apparent when you’ve been helped. The answer will also be discoverable, so others can find the discussion later.
- Messy code is a natural side effect of change; don’t blame developers for the untidiness. This drift toward disarray is known as software entropy. Many things cause software entropy. Developers misunderstand each other’s code or differ in style. Evolving technical stacks and product requirements cause chaos (see Chapter 11). Bug fixes and performance optimizations introduce complexity.
- Technical debt is a major cause of software entropy. Technical debt is future work that’s owed to fix shortcomings in existing code. Like financial debt, technical debt has principal and interest. The principal is the original shortcoming that needs to be fixed. Interest is paid as code evolves without addressing the underlying shortcoming—increasingly complex workarounds are implemented.
- Table 3-1: Technical Debt Matrix Reckless Prudent Deliberate “We don’t have time for design.” “Let’s ship now and deal with consequences.” Inadvertent “What’s layering?” “Now we know how we should’ve done it.” Source: https://martinfowler.com/bliki/TechnicalDebtQuadrant.html Prudent, deliberate debt is the classic form of tech debt: a pragmatic trade-off between a known shortcoming in the code and speed of delivery. This is good debt as long as the team is disciplined about addressing it later. Reckless, deliberate debt is created when teams are under pressure to deliver. “Just” is a hint that reckless debt is being discussed: “We can just add structured logging later,” or, “Just increase the timeout.” Reckless, inadvertent debt comes from unknown unknowns. You can mitigate the danger of recklessly inadvertent debt by preemptively writing down and getting feedback on implementation plans and doing code reviews. Continuous learning also minimizes inadvertent recklessness. Prudent, inadvertent debt is a natural outcome of growing experience. Some lessons are only learned in hindsight: “We should have created user accounts even for people who didn’t complete the sign-up flow. Marketing needs to capture failed sign-ups, and now we have to add extra code that could’ve been avoided if it was part of the core data model.” Unlike prudent and deliberate debt, the team will not know it’s taking on debt. Unlike inadvertent, reckless debt, this type of debt is more of a natural outcome of learning about the problem domain or growing as a software architect—not the result of simply not doing one’s homework. Healthy teams use practices such as project retrospectives to discover inadvertent debt and discuss when and whether to pay it down.
- Clean things up and do minor refactoring as you go. Make changes in small, independent commits and pull requests.
- If you have suggestions for large refactoring or rewriting, make the case to your team first. The following is a good framework for discussing technical debt: State the situation factually. Describe the risk and cost of the debt. Propose a solution. Discuss alternatives (including not taking action). Weigh the trade-offs. Make your proposal in writing. Do not base your appeal on a value judgment (“this code is old and ugly”). Focus on the cost of the debt and the benefit of fixing it. Be specific, and don’t be surprised if you are asked to demonstrate the benefits after the work is done.
- In his book Working Effectively with Legacy Code (Pearson, 2004), Michael C. Feathers proposes the following steps to safely modify existing codebases: 
    1. Identify change points. 
    2. Find test points. 
    3. Break dependencies. 
    5. Write tests. 
    6. Make changes and refactor.
- As you fix bugs or add features, clean adjacent code. Don’t go out of your way to find dirty code. Be opportunistic. Try to keep the code-cleanup commits separate from your behavior-changing commits. Separating commits makes it easier to revert code changes without losing code-cleanup commits. Smaller commits also make changes easier to review.
- If you want to rewrite code or diverge from standards, your improvement must be an order of magnitude better. Small gains aren’t enough—the cost is too high.
- New technology has a greater benefit if it makes your company more competitive. If it can be adopted widely, more teams will benefit, and your company will have less software to maintain overall.
- Expose logging, metrics, and call trace information for easy diagnostics.
- Perform null checks at the beginning of methods. Use NotNull annotations and similar language features when available. Validating up front that variables aren’t null means that later code can safely assume that it’s dealing with real values; this will keep your code cleaner and more legible. The null object pattern uses objects in lieu of null values. An example of this pattern is a search method that returns an empty list instead of null when no objects are found. Returning an empty list allows callers to safely iterate over the results, without special code to handle empty result sets.
- Constrain the values that variables can take. For example, variables with only a few valid string values should be an Enum rather than a String. Constraining variables will ensure that unexpected values will immediately fail (or might not even compile) rather than cause bugs.
- Never trust the input your code receives. Developers, faulty hardware, and human error can mangle input data. Protect your code by validating that its input is well formed. Use preconditions, checksum and validate data, use security best practices, and use tools to find common errors. Reject bad input as early as possible.
- When calling code that might throw exceptions, either handle them completely or propagate them up the stack.
- Don’t blindly retry all failed calls, particularly ones that write data or cause some business process to execute. It is better to let the application crash when it encounters an error it was not designed to handle; this is called failing fast. If you fail fast, no further damage will be done, and a human can figure out the correct course of action. Make sure to fail not only fast but also loudly. Relevant information should be visible so that debugging is easy.
- An __idempotent operation__ is one that can be applied multiple times and still yield the same outcome. Adding a value to a set is idempotent. No matter how many times the value is added, it exists in the set once. Remote APIs can be made idempotent by allowing clients to supply a unique ID for each request. When a client retries, it supplies the same unique ID as its failed attempt; the server can then de-duplicate the request if it’s already been processed. Making all your operations idempotent greatly simplifies system interactions and eliminates a large class of possible errors.
- Logging frameworks have log levels, which let operators filter messages based on importance. When an operator sets a log level, all logs at or above the level will be emitted, while messages from lower levels will be silenced.
- Application metrics are aggregated into centralized observability systems like Datadog, LogicMonitor, or Prometheus. Observability is a concept from control theory that defines how easy it is to determine the state of a system by looking at its outputs.
- Measure all of the following data structures, operations, and behaviors: 
    - Resource pools 
    - Caches 
    - Data structures 
    - CPU-intensive operations 
    - I/O-intensive operations 
    - Data size 
    - Exceptions and errors 
    - Remote requests and responses
- Do not get creative with configuration—use the simplest possible approach that will work. A static configuration file in a single standard format is ideal.
- Log all (nonsecret) configuration immediately upon startup to show what the application is seeing.
- Always validate configuration values when they’re loaded. Do the validation only once, as early as possible (right after the configuration is loaded).
- semantic versioning (SemVer), one of the most commonly used versioning schemes. The official SemVer specification is available at https://semver.org/. The spec defines three numbers: the major, minor, and patch version (sometimes called the micro version). Version numbers are combined into a single MAJOR.MINOR.PATCH version number.
- Patch versions are incremented for backward-compatible bug fixes. Minor versions are incremented for backward-compatible features. Major versions are incremented for backward-incompatible changes.
- Tests serve as a form of documentation, illustrating how the code is meant to be interacted with. They are the first place an experienced programmer starts reading to understand a new codebase.
- Mocking libraries are commonly used in unit tests, particularly in object-oriented code. Code often depends on external systems, libraries, or objects. Mocks replace external dependencies with stubs that mimic the interface provided by the real system. Mocks implement functionality required for the test by responding to inputs with hard-coded responses.
- Take advantage of tools that help you write quality code. Tools that enforce code quality rules are called linters. Linters run static analysis and perform style checks.
- __Deterministic code__ always produces the same output for the same input. By contrast, __nondeterministic code__ can return different results for the same inputs. A unit test that invokes a call to a remote web service on a network socket is nondeterministic; if the network fails, the test will fail. Nondeterministic tests are a problem that plague many projects.
- Don’t begin a review by leaving comments; first read and ask questions. Code reviews are most valuable if the reviewer really takes the time to understand the proposed changes. Aim to understand why a change is being made, how code used to behave, and how code behaves after the change. Consider long-term implications of the API design, data structures, and other key decisions.
- Give feedback on a change’s correctness, implementation, maintainability, legibility, and security. Point out code that violates style guides, is hard to read, or is confusing. Read tests and look for bugs to verify code correctness. Ask yourself how you would implement the changes to trigger alternative ideas and discuss the trade-offs.
- Google’s “Code Review Developer Guide” at https://google.github.io/eng-practices/review/ is a good example of a company’s code review culture.
- To avoid failed partial deployments, make deployment all or nothing (atomic). A partially deployed install should never partially replace the previous successful install, and it should be possible to install the same package to the same machine multiple times, even if previous installation attempts terminated abruptly. The easiest way to make deployments atomic is by installing software in a different location than the old version; don’t overwrite anything. Once packages are installed, a single shortcut or symbolic link can be flipped atomically. Installing packages in a new location has the added benefit that rollbacks become much easier—just point to the old version again. In some cases, different versions of the same software can be run simultaneously on the same machine!
- There are many rollout strategies: 
    - feature flags - Feature flags allow you to control what percentage of users receive one code path versus another. 
    - circuit breakers - Circuit breakers automatically switch code paths when there’s trouble. 
    - dark launches
    - canary deployments
    - blue-green deployments 
        - Dark launches, canary deployments, and blue-green deployments let you run multiple deployed versions of your software simultaneously.
- Google Cloud’s support priority ladder offers one example of how priority levels may be defined (https://cloud.google.com/support/docs/best-practice#setting_the_priority_and_escalating/): 
    - P1: Critical Impact—Service Unusable in Production 
    - P2: High Impact—Service Use Severely Impaired 
    - P3: Medium Impact—Service Use Partially Impaired 
    - P4: Low Impact—Service Fully Usable
- Incident response is broken into these five steps: 
    1. Triage: Engineers must find the problem, decide its severity, and determine who can fix it. 
    2. Coordination: Teams (and potentially customers) must be notified of the issue. If the on-call can’t fix the problem themselves, they must alert those who can. 
    3. Mitigation: Engineers must get things stable as quickly as possible. Mitigation is not a long-term fix; you are just trying to “stop the bleeding.” Problems can be mitigated by rolling back a release, failing over to another environment, turning off misbehaving features, or adding hardware resources. 
    4. Resolution: After the problem is mitigated, engineers have some time to breathe, think, and work toward a resolution. Engineers continue to investigate the problem to determine and address underlying issues. The incident is resolved once the immediate problem has been fixed.
    5. Follow-up: An investigation is conducted into the root cause—why it happened in the first place. If the incident was severe, a formal postmortem, or retrospective, is conducted. Follow-up tasks are created to prevent the root cause (or causes) from happening again. Teams look for any gaps in process, tooling, or documentation. The incident is not considered done until all follow-up tasks have been completed.
- Track communication in written form in a central location: a ticketing system or chat. Communicating helps everyone track progress, saves you from constantly answering status questions, prevents duplicate work, and enables others to provide helpful suggestions. Share both your observations and your actions, and state what you are about to do before you do it. Communicate your work even if you are working alone—someone might join later and find the log helpful, and a detailed record will help to reconstruct the timeline afterward.
- Runbooks are predefined step-by-step instructions to mitigate common problems and perform actions such as restarts and rollbacks.
- Use the scientific method to troubleshoot technical problems. Chapter 12 of Google’s Site Reliability Engineering book offers a hypothetico-deductive model of the scientific method. Examine the problem, make a diagnosis, and then test and treat. If the treatment is successful, the problem is cured; if not, you reexamine and start again.
- There are many approaches and templates for writing a postmortem. One good example is Atlassian’s postmortem template (https://www.atlassian.com/incident-management/postmortem/templates/). The template has sections and examples describing the lead-up, fault, impact, detection, response, recovery, timeline, root cause, lessons learned, and corrective actions needed.
- A critical section of any postmortem document is the root-cause analysis (RCA) section. Root-cause analysis is performed using the five whys. This technique is pretty simple: keep asking why. Take a problem and ask why it happened. When you get an answer, ask why again. Keep asking why until you get to the root cause. The “five” is anecdotal—most problems take about five iterations to get to the root cause.
- “What happens if we don’t solve this problem?” is a powerful question. When the stakeholder answers, ask if the outcome is acceptable. You’ll find many problems don’t actually need to be solved.
- Design spikes are a good way to manage the tension between creative work and predictable delivery. A spike is an Extreme Programming (XP) term for a time-bounded investigation. Allocating a spike task in a sprint will give you space to do deep thought without having other tasks to worry about.
- Not every change requires a design document, much less a formal design review process. Your organization may have its own guidelines for this; absent those, use these three criteria to decide if a design document is required: The project will require at least a month of engineering work. The change will have long-lasting implications with regard to extending and maintaining the software. The change will significantly impact other teams.
- Design documents are particularly helpful for engineers new to the team. Without design documents, engineers find themselves crawling through code, creating box diagrams, and teasing knowledge out of senior engineers to understand what’s going on. Reading a trove of design documents is far more efficient.
- Version control your design documents. A good trick is to keep design documents version controlled in the same repository as code. Code reviews can then be used as a review for design comments. The documents can also be updated as code evolves.
- Design document should describe the current code design, the motivation for a change, potential solutions, and a proposed solution. The document should include details about the proposed solution: architectural diagrams, important algorithmic details, public APIs, schemas, trade-offs with alternatives, assumptions, and dependencies.
- Richard Hickey, author of Clojure, gives a “field report” on software design in his talk “Hammock Driven Development” (https://youtu.be/f84n5oFoZBc/). Hickey’s talk is one of the best introductions we’ve seen to the messy process of software design. Use large open source projects to see real-world design in progress. Python Enhancement Proposals (https://github.com/python/peps/), Kafka Improvement Proposals (https://cwiki.apache.org/confluence/display/KAFKA/Kafka+Improvement+Proposals/), and Rust Request for Comments (RFCs) (https://github.com/rust-lang/rfcs/) are good illustrations of real-world design. For a glimpse of internal design processes, WePay’s engineering blog has a post, “Effective Software Design Documents” (https://wecode.wepay.com/posts/effective-software-design-documents). The post describes WePay’s approach to design and how it’s evolved over the years. The design template that WePay has used for hundreds of internal designs is available on GitHub (https://github.com/wepay/design_doc_template/).
- Faced with unknown future requirements, engineers usually choose one of two tactics: 1. they try to guess what they’ll need in the future, or 2. they build abstractions as an escape hatch to make subsequent code changes easier. 
    - Don’t play this game; both approaches lead to complexity. Keep things simple (known as KISS—keep it simple, stupid
- The easiest way to keep code simple is to avoid writing it altogether. Tell __yourself that you ain’t gonna need it__ (YAGNI). When you do write code, use the principle of least astonishment and encapsulation. These design principles will keep your code easy to evolve.
- Counterintuitively, short method and variable names actually increase cognitive load. Specific, longer method names are more descriptive and easier to understand.
- Don’t couple database and application lifecycles. Tying schema migrations to application deployment is dangerous. Schema changes are delicate and can have serious performance implications. Separating database migrations from application deployment lets you control when schema changes go out.
- Liquibase is just one tool that can manage database migrations; there are others like Flyway and Alembic. Many object-resource mappers (ORMs) come with schema migration managers as well.
- According to The Papers of Dwight David Eisenhower, Volume XI, Eisenhower said, “In preparing for battle I have always found that plans are useless, but planning is indispensable” (Johns Hopkins University Press, 1984). This applies to roadmaps. We’ve never seen a yearly or even quarterly roadmap be 100 percent accurate; this isn’t the point. Roadmaps should encourage everyone to think long-term about what the team is building; they’re not meant to be static and reliable documents about what the team will build nine months later. Quarters that are farther away should be fuzzier, while quarters that are closer should be more accurate. Don’t fool yourself into thinking any quarter is 100 percent accurate.
- you set the agenda in a 1:1, and 1:1s are not for status updates.
- Don’t make the key results a to-do list. They should spell out not how to do something but rather how you’ll know when something is done. There are many ways to reach an objective, and your OKRs should not box you into a particular plan.
- OKRs are commonly set slightly higher than reasonable to create “reach” or “stretch” goals. This philosophy implies that you should not complete 100 percent of your reach-goal OKRs; this is a sign that you aren’t shooting high enough. Most OKR implementations shoot for a 60 percent to 80 percent success rate, meaning 60 to 80 percent of the objectives are met. If you’re hitting more than 80 percent of your objectives, you’re not being ambitious; below 60 percent and you’re not being realistic or are failing to meet expectations.
- Use the Situation-Behavior-Impact (SBI) framework when providing feedback. First describe the situation. Then, describe the behavior: a specific behavior you find praiseworthy or problematic. Finally, explain the impact: the effect of the behavior and the reason it’s important.
- We first encountered the concept of T-shaped people in Valve’s Handbook for New Employees (https://www.valvesoftware.com/en/publications/).