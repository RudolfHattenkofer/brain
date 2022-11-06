## Too many DB connections?

[https://koaware.com/sidekiq/failures](https://koaware.com/sidekiq/failures) indicates that maximum number of connections was reached. Initial situation:

- user-auth is using 30 connections
- koaware is using 56

…that seems like a lot!

Scaled builder service to 1 replica instead of 2

Scaled koaware service to 2 replicas instead of 4

Why is user-auth using 30?!

There is usually very few requests to this service

Set max*threads to 2 instead of 4, set min*threads to 1 instead of 4

Result:

- koaware is using 32
- user-auth is using 17

That is still a lot for user-auth, it should only be using a few (below 10)

Weird observation: user-auth went down when koaware main service was scaled down. Are credentials reused somewhere?

For now this should do.



