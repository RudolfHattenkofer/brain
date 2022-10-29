The perfect infrastructure setup doesn't exist. There is always going to be a lock-in effect. The delicate balance is to abstract away complex lock-ins in software to still benefit from a providers functionality, while minimizing the migration cost.

Lock-in cost = Opportunity - Migration cost

This should be a net benefit for any good infrastructure choice.

Some practical trade-offs might be:

- Using common primitives (containers, task queues etc) that have provider specific implementations, but are conceptually similar enough to swap out if need be
- Slightly higher lock in for reduced operational overhead



