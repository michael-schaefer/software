# The Bottleneck Is Shifting

Lean thinking says: find the bottleneck and optimize there. Everything else is local optimization that doesn't improve the system. If you speed up a non-bottleneck step, you don't get more throughput — you get more inventory piling up in front of the real constraint.

For the past several decades, the bottleneck in software development has been **building software**. Writing code, getting it to compile, integrating it, testing it, fixing the bugs. The entire industry — its processes, team structures, tools, and career paths — is organized around the assumption that production is the constraint.

AI is removing that constraint. And when a bottleneck moves, everything organized around the old bottleneck becomes misaligned.

## The Value Stream

To see where the bottleneck is going, map the full value stream of software development — from customer need to working software in production:

1. **Understand the problem.** What does the user actually need? What's the pain? What does success look like?
2. **Define the solution.** What should we build? What are the requirements, acceptance criteria, constraints?
3. **Design the architecture.** How should the system be structured? What are the components and their relationships?
4. **Write the code.** Produce the software. ← *The traditional bottleneck.*
5. **Verify correctness.** Test it. Review it. Confirm it's secure, correct, and does what was intended.
6. **Deploy.** Get it to production.
7. **Monitor.** Is it working? Is it performing? Are there errors?
8. **Get feedback.** Did it actually solve the problem? What did we learn? What needs to change?

Steps 6 and 7 were already largely automated by the DevOps movement. CI/CD pipelines, infrastructure as code, observability platforms — these compressed deployment and monitoring from weeks to minutes.

AI is now compressing step 4. What used to take a team of developers two weeks in a sprint can now take one person an afternoon. Code generation that was the primary consumer of engineering time is becoming fast and cheap.

That leaves the bottleneck sliding in two directions: **upstream** to problem understanding and definition, and **downstream** to verification.

## Upstream: Knowing What to Build

Steps 1 and 2 — understanding the problem and defining the solution — were always important. But they were masked as bottlenecks because building was so slow.

When it takes two weeks to build something, you get one shot per sprint. The cost of getting requirements wrong is high, but the cost of getting requirements *exactly* right is also high — so teams settled for "good enough" requirements and course-corrected over multiple sprints. The slowness of building provided a natural throttle. You couldn't build the wrong thing *that fast*.

AI removes the throttle. You can now generate working software from vague requirements in hours. And vague requirements produce vague software — fast. The quality of the input becomes the limiting factor. If you don't know precisely what you want, AI will happily build you something that precisely matches your imprecision.

This means the skills around problem understanding — customer discovery, requirements elicitation, domain expertise, product thinking — become the upstream bottleneck. Not because they're new, but because the step that used to be slower than them (building) no longer is.

## Downstream: Verifying What Was Built

Step 5 — verification — was manageable when humans wrote all the code. A team might produce a few hundred lines of carefully considered code per day. Code review, testing, and QA could keep pace because the production rate was naturally throttled by human typing and thinking speed.

AI changes the ratio. A single developer with AI can produce thousands of lines of code in an hour. The code may be correct. It may not. It may be subtly wrong in ways that pass superficial review. And unlike human-written code, there's no author who reasoned through each decision and can explain why a particular approach was chosen.

Verification becomes the downstream bottleneck:

- **Code review doesn't scale.** If one person generates 10x more code, the reviewers are now the constraint. And the code is harder to review because the reviewer doesn't have the author's mental model of why decisions were made.
- **Testing becomes critical, not optional.** When code is cheap to produce, tests are the primary evidence that it works correctly. A codebase with AI-generated implementation and human-written tests is arguably better understood than one where humans wrote everything but skipped the tests.
- **Security review gets harder.** AI-generated code may introduce vulnerabilities that a human author would have caught through domain knowledge. Automated security scanning helps, but it's not a complete solution.
- **Understanding lags behind output.** You can accept AI-generated code faster than you can understand it. The delta between "code that exists" and "code someone understands" grows over time. This is the comprehension debt problem.

## The Scrum Misalignment

Scrum's team structure reveals its assumption about where the bottleneck is.

A typical Scrum team: 6-8 developers, 1 QA engineer, 1 product owner, 1 scrum master. That's roughly an 8:1 ratio of builders to definers. The entire ceremony structure orbits around production:

- **Sprint planning:** Decide what to build.
- **Daily standup:** Coordinate the building.
- **Sprint review:** Show what was built.
- **Retrospective:** Improve how we build.

Every ritual is a production-management ritual. There's no ceremony for "did we understand the problem correctly?" There's no ceremony for "do we actually understand the code we just shipped?" The process assumes the hard part is building, and everything else is subordinate.

If the bottleneck is no longer building, this structure is misaligned:

**The team ratio might need to invert.** If one developer with AI can do the production work that previously required six, you don't need six developers. You might need more product people who deeply understand the problem, more QA/verification capacity, more people focused on understanding and evaluating rather than typing. The 8:1 builder-to-definer ratio may need to become 2:1 — or even 1:2.

**The sprint cadence may be the wrong unit.** A two-week sprint was the shortest practical cycle when building was slow. You needed two weeks for the team to plan, build, test, and demo. If the building step compresses from two weeks to two days (or two hours), the sprint is mostly waiting. The feedback loop should match the pace of the bottleneck, not the pace of a constraint that no longer exists.

**Standups lose their purpose.** Daily standups exist to coordinate parallel work streams during a sprint. If a small number of people can produce the same output, the coordination overhead drops. The standup becomes a ritual performed out of habit, not out of need.

**Story points measure the wrong thing.** Story points estimate the effort to *build* something. If building effort approaches zero, story points lose their meaning. What matters is the effort to *define* the requirement clearly enough to generate correctly, and the effort to *verify* the output. Neither of these is what story points traditionally measure.

## Where the Bottleneck Is Going

The pattern is clear if you follow the Lean logic:

| Era | Bottleneck | Organized Response |
|---|---|---|
| Pre-Agile (Waterfall) | Coordination — large teams couldn't stay aligned | Heavy planning, detailed specifications, phase gates |
| Agile/Scrum | Production — building software was slow and expensive | Small teams, sprints, iterative delivery |
| DevOps | Deployment — code was done but couldn't get to production | CI/CD, infrastructure as code, automated pipelines |
| AI Era | Judgment — knowing what to build and whether it's right | *This is what we need to figure out* |

Each era identified the real bottleneck and restructured around it. We're in the early days of the AI era, and most organizations are still structured for the production bottleneck. They're adding AI to make developers faster, but they haven't restructured teams, processes, or roles to address the bottleneck that emerges once building is no longer the constraint.

## What Restructuring Looks Like

If the bottleneck is judgment — upstream problem-understanding and downstream verification — then the organization should optimize for judgment:

**Invest more in defining the problem.** Spend more time (proportionally) on customer discovery, requirements refinement, and acceptance criteria. The ROI of a precisely defined requirement goes up dramatically when AI can translate a good requirement into working software in hours. A vague requirement wastes minutes of generation time and hours of debugging time.

**Invest more in verification.** If code is cheap to produce, make verification the primary engineering activity — not an afterthought. This means more testing, more review capacity, more automated quality checks, and a culture that values "I verified this thoroughly" as much as "I built this quickly."

**Shrink teams, deepen expertise.** A small team of people who deeply understand the domain, the customer, and the codebase — amplified by AI — may outperform a large team of generalists doing sprint work. Depth of understanding is the scarce resource, not person-hours of coding.

**Shorten the feedback loop beyond the sprint.** If building takes hours, get feedback in hours. Don't wait for a sprint review two weeks from now. Show the working software to stakeholders the same day it's generated. The faster the feedback, the less waste from building the wrong thing.

**Measure what matters.** Stop measuring velocity (story points per sprint) and start measuring cycle time (time from identified need to validated solution in production). Velocity measures production speed. Cycle time measures the whole system, including the new bottlenecks.

The organizations that figure this out first will have a significant advantage — not because they generate code faster, but because they'll be structured to *use* that speed without drowning in unverified, misunderstood output.
