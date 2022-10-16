[All Hands on Deck - Slack Engineering](https://slack.engineering/all-hands-on-deck/)

- Reliability Engineering!
- Modeled after FEMA incident response guidelines
- Each team responsible for running their code → DevOps

Technical writeup: [https://slack.engineering/a-terrible-horrible-no-good-very-bad-day-at-slack/](https://slack.engineering/a-terrible-horrible-no-good-very-bad-day-at-slack/)

## Timeline

The timeline of an incident is composed of four distinct stages, **Customer Impact**, **Operations Impact**, **Learning & Prevention.** Within these stages, there are distinct operations that lead to the final resolution of an incident, which we’ll briefly summarize.

**Detect:** Detection of a regression or customer impact via, ideally, SLO failure, automated alerts driven by metrics, or less ideally, customer reports.

**Assemble:** The Subject Matter Expert (SME) who gets the initial **Detect** page will invoke the Assemble process and alert the Incident Commander on-call.

**Verify:** Incident Commander discusses with SME on initial scope of the impact as well as severity. Our first Conditions, Actions and Needs (CAN) reports can begin.

**Dispatch:** Incident Commander, based on the CAN report, will page additional SME’s as needed.

**Mitigate:** A diagnosis is presented, and a mitigation action is proposed & executed.

**Repair:** Typically, mitigations are temporary — an analogy would be duct-taping a leak. The repair action is a long term fix if needed.

**Review:** The Incident Review process kicks off and we review the incident and extract lessons and action items from it.

**Action Items:** We complete action items based on priority within defined SLA’s to further enhance prevention of the incident recurring.



