title=What is Shiro?
type=page
tags=documentation, about
status=published
~~~~~~

Apache Shiro is an application security framework that provides application developers very clean and simple ways of supporting four cornerstones of security in their applications: authentication, authorization, enterprise session management and cryptography.

<a name="WhatisShiro-MissionStatement"></a>
## Mission Statement

We believe:

- Java security should be <em>really easy</em> to understand and use in your own applications.
- Existing Java security mechanisms (like JAAS) are too confusing and fall way short in the area of application-level security.
- Authentication and Authorization functionality should be as pluggable and flexible as possible.
- Authentication and Authorization are only half of a robust security framework. Enterprise Session Management and easy Cryptography services are the other half.
- <b>Session Management should not be tied to web or EJB applications</b>.  We believe Sessions are a business-tier concern that should be accessible in any client or server environment.
- Heterogeneous client mediums (HTTP requests, Applets, Java Web Start, C# applications, etc) should be able to participate in the same Session, regardless of the client technology.
- Security code should be eliminated as much as possible in favor of a cleaner declarative security model utilizing JDK 1.5 Annotations or XML, whichever you prefer.
- Last but definitely not least,  a security framework should support a <em>dynamic</em>, <em>instance-level</em> security model out-of-the-box (i.e. changing user/group/role/permission assignments <em>during runtime</em>)

We will:

- Create a security framework that is <em>extremely</em> easy to use and understand.  An evaluating developer should grasp all the fundamentals within 10 minutes.
- Employ an interface-driven POJO-based OO design with extreme flexibility, pluggability and customization in mind.
- Develop a production-quality implementation that can be used in any deployment environment, from the simplest Applet to the largest high-availability clustered enterprise applications.
- Foster a positive open-source developer community, listening to suggestions and requests in order to provide the highest quality security framework available for Java.


<a name="WhatisShiro-ProjectHistory"></a>
## Project History

<em>by Les Hazlewood</em>

Apache Shiro, like most useful  tools, was created out of necessity.  About 20% of clients I worked with needed to support a <em>dynamic</em> security model, where an administrator could assign users to groups and roles, and assign permissions to roles, and change all of this during runtime in a nice gui and/or web page.

Standard JAAS and EJB security models couldn't cut it - they required static definitions that only programmers could change, requiring the application to re-deployed all over again. And although those 20% of clients required dynamic functionality, there were many more that would have liked that capability, even though it wasn't a pure requirement for their applications. I quickly realized how useful something like this was and tried to see how I could achieve what many people wanted.

Like most of the Java community, I looked into [JAAS](http://docs.oracle.com/javase/7/docs/technotes/guides/security/jaas/JAASRefGuide.html) to see if it could do what I wanted. After all, it was really the only security technology out there widely accessible to Java developers at the time. I did a <em>lot</em> of research, looking for ways that I might be able to coerce JAAS into doing what I wanted. Sometimes it came close. JAAS Authentication could meet my needs with a decent amount of effort, but JAAS Authorization didn't even come close.

JAAS is tied too heavily tied to virtual machine-level concerns. As an application architect, I usually didn't care one bit about whether or not a <em>Class</em> could execute inside the virtual machine.  What I really wanted to control is whether or not the <em>current user</em> could execute a given method, often based on the method's arguments. So, I hobbled a bit, creating some functionality to piggy-back JAAS and custom-coded the rest. The result was only usable on a few applications and wasn't nearly as robust as I wanted.

Then I came to work on a really great application that pushed the limits of application security. This application was written for government organizations and needed <em>extremely</em> powerful yet flexible security support.  The client required the following:

* Traditional log-in/log-out functionality, with pluggable back-end support (no big deal)
* Customization of users, roles and permissions <em>during runtime</em> (a big deal)
* The ability to restrict not only what functionality was available to a user, but also what was available <em>on the machine they were using</em> (flexible authorization model).
* The ability to participate in the <em>same session</em> when visiting a web page, when using an embedded Java Applet, or when making a remote EJB call (a very big deal)
* The ability to dynamically change the security model during runtime such that the following would be possible (this is really cool):
    1. A user clicks a button that alters the state of a piece of hardware affecting a _lot_ of people.
    2. An administrator determines the user is potentially a high-risk employee (disgruntled, unstable, whatever), and changes that user's permissions to prevent them from clicking that button again.
    3. The very next instant, the same user clicks the same button again to alter the hardware's state (this time perhaps to do something that isn't very nice).
    4. Because the user's permissions were changed, the second button click fails and shows them a nice error message explaining that they don't have permission for the operation.
All of this could happen without requiring the user to log-out and then log back in again to acquire a new set of roles and/or permissions. Security changes had to be <em>instantaneous</em>.



I looked at all of these requirements, and although a little extreme for most applications, I knew that there were a lot of other developers out there that could benefit from a framework that could do all of these things, even if they didn't use them all.

I knew I would need to use this functionality again in some capacity or another, so I founded Apache Shiro's predecessor project, named 'JSecurity' in 2004 to solve all of these issues. This time though, the project team began to build an incredibly clean Object-Oriented architecture from scratch, keeping change and flexibility in mind. Nearly every facet of Authentication, Authorization, transparent Session Management and Cryptography are customizable and pluggable. After moving to the Apache Software Foundation, we renamed the project to Apache Shiro.

Perhaps best of all, Apache Shiro is POJO and interface based. You can use it in any pojo container, servlet container, J2EE application server, or standalone application out of the box. And, we currently have some projects in the works to make integration into the most popular containers and servers as easy as possible.

Well, that's how the JSecurity project and then Apache Shiro was started. We're always looking to improve. Since Shiro is open-source, please think about joining the project or helping out, even if you just offer suggestions. Anything is appreciated!

Best regards,

Les Hazlewood
