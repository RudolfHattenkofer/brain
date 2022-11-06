[Google Cloud Platform](https://accounts.google.com/ServiceLogin?service=cloudconsole&passive=1209600&osid=1&continue=https://console.cloud.google.com/kubernetes/deployment/us-central1-a/main/default/main/overview?project%3Dkoaware-prod%26pageState%3D(%2522savedViews%2522:(%2522i%2522:%2522872b7ea6e16a4c628335bea9348c9b3a%2522,%2522c%2522:%255B%255D,%2522n%2522:%255B%255D),%2522deployment_overview_active_revisions_table%2522:(%2522r%2522:50))&followup=https://console.cloud.google.com/kubernetes/deployment/us-central1-a/main/default/main/overview?project%3Dkoaware-prod%26pageState%3D(%2522savedViews%2522:(%2522i%2522:%2522872b7ea6e16a4c628335bea9348c9b3a%2522,%2522c%2522:%255B%255D,%2522n%2522:%255B%255D),%2522deployment_overview_active_revisions_table%2522:(%2522r%2522:50)))

→ Little warning icon: Pod most likely not starting! No specific error message though.

Here is how I want to make sure it never happens again: There is a new line in the Dockerfile with a "health check". It's a simple task that loads all code in your project, and will fail on any errors right in the building phase! That means that this category of error will show up in circleci and not drive you mad when things don't show up in prod Here are the changes I made:

[https://github.com/Koaware/koaware/compare/5a5f9b5e83d844e945cc238a29036bffd99b50ff...39e939e453799cb21a9dd46164b96a977389e1a7](https://github.com/Koaware/koaware/compare/5a5f9b5e83d844e945cc238a29036bffd99b50ff...39e939e453799cb21a9dd46164b96a977389e1a7)

This is what circleci looks like with such an error:

[https://app.circleci.com/pipelines/github/Koaware/koaware/397/workflows/da7b1636-69cc-4b4f-881c-4a4fb5e5748e/jobs/2521](https://app.circleci.com/pipelines/github/Koaware/koaware/397/workflows/da7b1636-69cc-4b4f-881c-4a4fb5e5748e/jobs/2521)

And here is the fix:

[https://github.com/Koaware/koaware/commit/557e28ca9fa3e67befab6ef7ffe721e0e562f660](https://github.com/Koaware/koaware/commit/557e28ca9fa3e67befab6ef7ffe721e0e562f660)

Side note: To make this possible, no code can access the database at load time. I added a couple of Rails.env.test? guards in events where I got an error "PG::ConnectionBad: could not translate host name "test" to address: Name does not resolve" in CircleCI. This is a code smell anyways, so try to avoid doing that in general

[https://github.com/Koaware/koaware/commit/2d26bb32fba9692775ecd57db5eb4a2e604cd4cd](https://github.com/Koaware/koaware/commit/2d26bb32fba9692775ecd57db5eb4a2e604cd4cd)



