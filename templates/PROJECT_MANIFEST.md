# PROJECT_MANIFEST — <project name>

Complete this privately. The owner approves the mission, authority and completion
gates before research. Amendments must record the date, authorizing direction and
reason; the worker may propose changes, not authorize its own expanded scope.

```yaml
CONTROL_FORMAT: EZF-1
PROJECT_ID: "<stable project identifier>"
DRIVE_ROOT_ID: "<private project folder ID>"
OWNERSHIP_CONTROL: "<enforced mechanism, protected writes and safe transfer>"
REPOSITORIES:
  - name: "<owner/repository>"
    write_actions: []
PUBLICATION_BOUNDARY: "none; research results remain in private Drive"
```

GitHub reads are limited to the named repositories. Empty `write_actions` means
read-only. Optional grants must name exact actions (for example, issue creation or
comments), allowed content and, for documentation PRs, allowed paths. Never infer
publication permission from repository access. The research worker has no code,
merge, release or repository-administration authority.

## Mission and deliverable

<One research outcome, its intended reader and the durable deliverable.>

## Scope and stopping rule

<Included questions, exclusions, source/time budget per unit, and the condition
for an inconclusive answer. State any evidence-triggered follow-up obligation;
otherwise do not invent endless research beyond the deliverable.>

## Completion gates

Every required question is answered or explicitly inconclusive. Every decision
cites its evidence and recorded contradictions. Each final output revision has a
PASS from a later review run and is usable without private conversational context.
Any required authorized publication is confirmed. <Add mission-specific gates.>

## Scheduling and oversight

<Owner/operator, intended cadence and timezone, who notices missing reports, and
acceptable silence. The owner, not the worker, manages task lifecycle. Record how
manual runs, retries and scheduled runs are excluded during another writer's work.
An unproved ownership mechanism is a setup gate, not permission to proceed.>
