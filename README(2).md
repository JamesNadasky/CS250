# CS 255: System Analysis and Design — DriverPass

This repository holds my work from CS 255 at Southern New Hampshire University:

- **Business Requirements Document** (Project One)
- **System Design Document** (Project Two): UML use case, activity, sequence, and class diagrams plus the technical requirements

## Reflection

**Briefly summarize the DriverPass project. Who was the client? What type of system did they want you to design?**

The client was DriverPass, a small driver training company owned by Liam, with Ian as the IT officer. They saw that a lot of people were failing their DMV driving tests and wanted to fill that gap with online classes, practice tests, and on-the-road lessons with their own drivers and cars. They asked for a web-based system, hosted in the cloud, where customers can sign up for one of three training packages, pay, and book, change, or cancel two-hour driving lessons. The secretary also needed to be able to do all of that for customers who call or walk in. Liam wanted to run the business from anywhere, download reports to work on offline, turn off packages himself, and see who made or changed every booking. That last one mattered because right now he has no way of knowing who is responsible when something goes wrong.

**What did you do particularly well?**

I think the strongest part of my work was keeping everything traceable back to what Liam and Ian actually said in the interview. Requirements like the activity log, the five-attempt account lockout, and letting the owner disable a package all appear in the requirements, show up again as use cases, and then appear as specific attributes and classes in the design (the `ActivityLog` class, `isActive` on `Package`, and hours tracked on `Enrollment` so a package can be split into two-hour reservations). I also designed the scheduling flow so that a driver or car can never be double-booked: the activity diagram loops back if a slot is taken, and the database design backs that up with a unique constraint on driver, car, date, and start time. I was also careful to explain the design in plain language for a non-technical client, especially when describing security and the limitations of the system.

**If you could choose one part of your work on these documents to revise, what would you pick? How would you improve it?**

I would revise the technical requirements section of the system design document. Right now a lot of the software choices are written as "for example, Java with Spring Boot or Node.js" or "AWS, Azure, or Google Cloud." That keeps options open, but it leaves the development team to make decisions that should be made during design. I would commit to one stack and one cloud provider and give a short reason for each based on cost, DriverPass's size, and what Ian would be able to support. I would also add rough monthly cost estimates for hosting and payment processing, since the budget is one of the open items I listed as a limitation. Finally, I would add activity diagrams for modifying and canceling a reservation, because those flows have their own edge cases (like refunding hours to the package) that the current diagrams don't show.

**How did you interpret the user's needs and implement them into your system design? Why is it so important to consider the user's needs when designing?**

I treated the interview transcript as the source for everything and tried not to add features nobody asked for. Each type of user got their own role and only the access their job needs: customers manage their own lessons and tests, drivers see their schedule and write lesson notes, the secretary handles phone and walk-in bookings, Liam gets reports and package controls, and Ian gets account management. Some needs were easy to miss, like keeping the phone and in-person booking option for customers who don't want to book online, or having the pickup and drop-off locations match. Thinking about the users is important because a system can meet every technical requirement and still fail if the people using it find it confusing or if it doesn't fit the way the business actually works. If I had designed only for online booking, for example, the secretary would have lost a core part of her job and DriverPass would have lost customers who prefer to call.

**How do you approach designing software? What techniques or strategies would you use in the future to analyze and design a system?**

I start by understanding the problem before thinking about any code: who the users are, what they need to do, and what limits the business is working within, like budget, staff, and the deadline. From there I separate functional requirements from nonfunctional ones and write them as clear "the system shall" statements that can be tested. Then I use UML to move from the outside in. Use case diagrams show who does what, activity and sequence diagrams work out how a single task flows and where it can go wrong, and the class diagram shows the data needed to support all of it. In the future I would keep using interviews and walking through the client's current process, and I would add techniques like user stories, quick prototypes or wireframes that the client can react to, and regular check-ins so misunderstandings get caught early instead of at the end. An iterative approach, where the client reviews smaller pieces as they are built, would also make it easier to adjust when their needs change.
