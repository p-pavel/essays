# Illusion of Control

This is a quick follow-up to my post "Scala vs Rust" ([1]), but the pattern I describe here seems to apply broadly across many tooling and programming language decisions.

Perhaps I'm mistaken—feel free to correct me—but I believe that many developers are driven by an illusion of control. They go to great lengths to ensure they can dictate every aspect of their program's execution upfront. However, not only is this practically impossible in most cases, but it’s also often counterproductive.

Think about it: your code is running on superscalar, out-of-order speculative, multi-core/multi-execution threads supercomputers with complex memory hierarchies, including NUMA under the control of non-real-time operating systems (most of the time). All these were designed for sheer throughput. How much control can you really exert at that level?

The Misunderstood Problem of GC

A frequent complaint I hear is about garbage collection (GC). Many argue that it introduces significant overhead, and they want explicit control over memory management instead.
In my experience, GC overhead is typically within 1%, and it solves countless problems that manual memory management would otherwise introduce. Let’s not forget that determining memory lifecycles is statically undecidable. Moreover, once you start building servers (or operating systems, for that matter), the notion of being truly “stateless” becomes a myth.

The Obsession with Static Binaries

Another hot topic is the insistence on producing static binaries. Frankly, I don’t see the appeal.
What’s the practical difference between packaging your app in a single folder (and optionally compressing it into a file) and using static linking? If you believe all your functionality is self-contained in a single static binary, you’re mistaken—just run ls /boot. Or, if you're using microservices, consider how many layers of external dependencies are part of that setup.

Understanding Over Illusions

I’m not against learning how things work—far from it. Understanding your tools deeply (e.g., how an OS or the JVM works) is invaluable. These systems were designed the way they are for good reasons. Garbage collection, for example, wasn’t invented because developers are lazy; it exists to make code composable and efficient.

If you believe that high levels of control are essential for general-purpose systems (excluding scenarios like microcontrollers or extremely resource-constrained environments), I’d love to hear your perspective. Let’s discuss!