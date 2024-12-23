# #Rust vs #Scala: Facts and Hype Welcome

This is not a language war. Let's stick to facts and share examples.

I recently came across another project being rewritten from Scala to Rust, and honestly, I’m surprised ([1]). 
People involved complain that they miss fs2 ([2]) (streaming library) and cats ([3]).

I’ll admit that Rust has unique advantages in certain areas: microcontrollers, OS kernels, resource-constrained systems, and ultra-low latency scenarios. In those contexts, Rust’s design makes a lot of sense.

But when it comes to general-purpose programming languages, Scala seems like the better choice to me. It offers:

- Better syntax: Clearer and more concise. This can be subjective so let's compare the examples
- Richer abstractions: A more expressive type system with features like higher-kinded types, path-dependent types, and implicit resolution (or the newer given/using mechanism).
- A JVM foundation: Scala’s primary platform isn’t just stable—it’s an ecosystem powerhouse. Hot code reloading, mature libraries, and decades of engineering have built something incredibly effective.

So, why the rewrites?

I’ll admit that I can’t reach the people who made this decision directly, so I’m turning to the wider audience here. What motivates rewriting a project in Rust instead of Scala?

Here’s my perspective:

- If most of your data is immutable (which is common in modern functional programming), Rust’s borrow checker doesn’t seem like a game-changer. There are other ways to encapsulate mutable state effectively.
- A lack of garbage collection is a huge disadvantage in most scenarios.
- Rust’s syntax feels more verbose.
- Rust’s type system, while solid, can’t match Scala’s expressiveness, especially for generic programming or advanced type-level abstractions.
- Rust lacks rule-based derivation mechanisms (Scala’s given/using) that reduce boilerplate and improve readability.
- ...

To Rust advocates: I genuinely invite discussion. If you have concrete examples of where Rust shines beyond the areas I outlined, I’d love to see them. Code examples, patterns, and practical considerations about effectiveness are more than welcome.

And here’s another question for consideration: If you’re starting a Greenfield project, why would you choose Rust over Scala?

[1] [Scala is the best on JVM and JVM is best to target](https://www.linkedin.com/posts/perikov_scala-is-the-best-system-programming-language-activity-7269039794834309122-3FvZ)
[2] [fs2 streaming library](https://fs2.io/#/guide)
[3] [Cats typeclasses](https://typelevel.org/cats/typeclasses.html)