# 9K developers working on a single monolith

There was a [post on LinkedIn](https://x.com/ChShersh/status/1867481305862045957):

> If you’re a start up with 10 developers, you don’t need microservices, and a monolith world work just fine.
> If you’re a big company with 9K engineers, there’s no way they all can work on a single monolith.

I think there's a terminological confusion on the term "monolith".

I define "monolith" as a "product running in a single address space".

Let me describe a practical method that will let (supposedly) 9K engineers to work on a single monolith.

1. Target JVM
2. Establish binary artifact management in the form of local Maven repository
3. Establish clear API/implementation separation (with separate semantic versioning)
4. Use decent programming language (Scala, Kotlin). Provide pure Java interfaces as needed
for interoperability and future-proofness
5. Use decent programming practices to avoid memory leaks and infinite loops
6. Target OSGi container (like Karaf). It will handle hot reloading, dependency resolution,
lifecycle management etc
7. Structure your code around declarative components providing OSGi services
8. Use OSGi serices like logging, configuration managenement etc
9. Structure your whole applications with versioned Karaf "features" with depenndencies
10. Use Cellar clustering to sync configuration if needed
11. Be stateless. Let distributed data solutions do their job (Hazelcast, SQL/NoSQL...)
12. Run one container per node. Scale horizontally.
13. Establish A/B/canary deployment schemes dedicating part of your containers to this

If bloomberg needs some consulting on this please don't hesitate to ping me.

If you have your ideas on how microservices are better than the solution described 
above - please comment.

