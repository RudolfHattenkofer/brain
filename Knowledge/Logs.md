Is one of the [[Knowledge/Three pillars of observability]].

Logs are immutable, timestamped events, typically as free form text with structured metadata. They form a very granular history of every noteworthy action taken by a [[Distributed system]].

In an ideal simple world, they tell a story of an event chronologically, with every important step along the way. What is important can vary wildly from case to case, and is typically controlled through the “log/debug level”. Log too few information, and weird occurrences cannot be explained easily; Logging too much can be an issue if the “story” gets convoluted, or it can impact logging cost.

In a [[Distributed system]], it becomes increasingly important to correlate events across actions; This might be for troubleshooting shared resources or rare occurrences that are not straightforward to reproduce in a dev environment.



