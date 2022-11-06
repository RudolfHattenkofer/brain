https://web.hypothes.is/jobs/engineering-values/

1. Ship quickly, but sustainably
Ship useful stuff to our users frequently, but responsibly, by way of small iterations and resilient conventions.

Keep your changes small
Small pull requests (PRs) lead to stronger code, faster iteration, sustainable velocity and a happier team.

Smaller PRs with well-structured commits are a kindness to your reviewers, who benefit from a lighter context-switching demand. Code review cycles are speedier and of higher quality: reviewers are able to evaluate the entire change, quickly, without undue cognitive fatigue or LGTM-overwhelm.

Smaller changes sharpen your focus, encouraging modular code with a purity of purpose. This in turn elicits clear code organization and can make coding and test-writing faster.

Iterate, deploy, repeat
Frequently ship iterative changes, using a reliable and non-intimidating deployment mechanism. Smaller releases make it easier to pinpoint a problem should something go awry, and are more straightforward to verify in our QA step. Deploying more often gets features and fixes to users fast, and avoids making giant leaps in (potentially) the wrong direction.

2. Keep it simple
Predictable, concise code that makes sense is easier to maintain and debug, and is less demanding on you and your colleagues.

Write clean code with minimal cleverness
Comprehensibility and resilience far outweigh cleverness. Arcane solutions are not a badge of honor, and understanding your code shouldn’t be a hazing ritual. Don’t be afraid to be boring. New problems do not typically require new technology, nor new architectures.

Consistent code helps us ship quickly and sensibly: common conventions and patterns speed everyone up. Experienced team members can understand and extend such code with greater ease, and new developers can get up to speed in a project faster.

Break it down
Iterate, against small milestones. Decompose complex problems into component tasks. Decompose again. Keep up your momentum, and recall that perfect is the enemy of the good. Small steps are smoother than great leaps.

Don’t overthink. Understand what your problem is—but also what it isn’t. Avoid over-generalizing for extrapolated, hazy future use cases (YAGNI) and premature optimization. Remember: other people are going to need to understand how this works, too. DRY it out. Sketch out your coding thoughts, tinker and adjust as needed, tidy up.

Too much solution, or solving the wrong thing (even if it seems more interesting), can inflate and muddle things and make you—or, as likely, your colleagues—miserable. Hone your scope sharply, and restrain the contextual footprint of your changes.

3. Communicate, communicate, communicate
Distributed teams require exquisite communication. The artifacts of good technical communication processes can leave way-finding breadcrumbs for future devs and users.

Explain your thinking
Show your mental model, especially when tackling complex tasks. Written, spoken or visual communication of a proposed approach helps you to structure your own thinking and promotes collaboration. Resulting artifacts create a reference trail for all involved parties and help you avoid having to re-explain yourself over time. Prototype, spike, gist, comment, and draft where helpful. Draw pictures, too, if that helps.

Make it obvious, in some persisted way, what’s going on. Make it easy for future developers to understand not just how something works, but why a change was made.

Talk about your ideas early. Rubber-ducky ideas with colleagues in ad-hoc interactions, or schedule a targeted chat with your team. Don’t surprise your colleagues with “big reveal” PRs. Use words, but not too many. When writing, re-read what you’ve typed up once or twice more (and edit) before sharing. Take care with the details—formatting, grammar and terminology—to increase your clarity and improve your colleagues’ reading comprehension.

Include context
Be aware of your own, transient frame of reference when solving a problem, and make sure that context doesn’t get lost. Where possible, bake the context into the changes themselves (comments, commit messages, other metadata), or refactor to reduce the scope of the context necessary. Documentation is nice, too, but has to be discoverable, and maintained—the closer the context lives to the changes themselves, the better.

Persisted context in the form of commit messages, PR threads, comments, and other artifacts prevent you from having to explain yourself from scratch and leaves a clear trail of history for future developers.

4. Lift the team and the community
Support your colleagues and the technical community: prioritize code reviews, offer help, listen to ideas and look out for opportunities to learn and teach.

We first
It can sound a little corny, but we are all on the same team here, trying to help each other be successful. Check your ego and avoid attachment to an approach: your worth is not tied up in a bit of code. Be willing to kill your darlings. Experiment with thinking we instead of I. Our default is transparency: we work in the open and we are open-source ambassadors.

Adhere to the team’s consensus-based process, but use just barely enough process. We should be aided by our tools and processes, not captive to them—it’s part of our job as a team to help find the right balance.

Review with care and humanity
Code reviews are business-critical—all production code requires review—and an important opportunity to support your teammates. Everyone involved, whether author or reviewer, has one core objective: help to move things forward.

As a reviewer, you are a partner in the success of the body of work. Make code reviews a top priority, and be thorough and compassionate. Commit yourself when you review: focus and take your time. Avoid dismissive terms like “simply”, “just.” Ask questions. Discuss the code, not the coder. There are many conventions and techniques at play in high-quality code reviews, but all involve common underpinnings: be responsive, be committed and be kind.

If you’re the code author, set your reviewer up for the best possible review cycle. Roll out the red carpet with a polished PR description. Do everything you can so that your reviewer can get down to the work of reviewing without fuss. Screenshots. Testing instructions. Comments to help them navigate. Remember to expect feedback—that’s the whole point—and to respond to it with the same humanity you expect from your reviewer.

5. Code with empathy
Empathetic development processes are welcoming to future contributors, allow for a diversity of perspective, and keep both immediate and future developer happiness in mind.

Leave it better than you found it
Write tests, always, and pay down tech debt as you encounter it, when feasible. It doesn’t have to be a slog. Cultivate simplicity and focus by letting our tools do the grunt work.

Well-crafted tests and broad coverage help to reduce regressions, while ongoing cleanup parcels out maintenance into more manageable chunks. Avoid “broken windows” by fixing code smells, code that bucks conventions and fragility as you go. If you can’t fix it now, track it for later.

Automate what you can—linting, formatting, tooling—to enforce (usually dull) stylistic consistency: leave your brain free to tackle the more important and interesting problems.

Promote coding happiness: present and future
Think long-scale. Be strategic in your design choices, even if it requires a little more cognitive juice up front.

At the same time, be present-minded, too. Use our values as a lens to help you spot over-design or unneeded complexity. Often the obvious and pragmatic option is the right one, or, at least, very much good enough.

Finding a balance between long- and short-term software-design goals can be both terrifically challenging and profoundly satisfying.