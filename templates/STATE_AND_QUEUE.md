# STATE_AND_QUEUE — <project name>

Complete privately. This is the canonical queue and current state, not a chat summary.
Read it before each run and update it only while write ownership is enforced.

```yaml
CONTROL_FORMAT: EZF-1
STATE_REVISION: 0
PROJECT_STATUS: SETUP
SETUP_STATUS: PENDING
CURRENT_UNIT: null
CURRENT_RUN_ID: null
CURRENT_UNIT_STATUS: null
LAST_COMMITTED_RUN_AT: null
LAST_RESULT: null
```

`PROJECT_STATUS`: SETUP, ACTIVE or COMPLETE. `SETUP_STATUS`: PENDING or READY.
`CURRENT_UNIT_STATUS`: null, CLAIMED or COMMITTING. `LAST_RESULT`: null, PROGRESSED,
BLOCKED or NO_WORK. These are logical records, not provider locks or proof of uptime.
Use `SETUP` and `NO_WORK` for operational outcomes, not research question IDs.
Move to ACTIVE only after verified setup.

## Setup receipt

<Record the observed execution context/identity and time, GitHub read result and
revision, Drive read/create/update/content-and-parent readback, and the actual
ownership mechanism and its limitations. Distinguish interactive from scheduled
trials. Missing or unknown mandatory capability keeps setup PENDING. Record scoped
safe evidence references, never credentials.>

## Queue

Replace the example with the first real question. Append IDs; never reuse or renumber
them. Queue order is priority among eligible questions. Keep completed records as the
ID and decision index, reading their artifacts only when relevant.

```yaml
- id: Q-001
  question: "<one answerable research question>"
  status: READY
  depends_on: []
  method: "<sources, comparison or measurement>"
  stop_condition: "<recognizable answer or bounded inconclusive result>"
  output: null
  review: null
  publication: null
```

Question status: READY, REVIEW, DONE or BLOCKED. `output` stores the artifact locator
and exact revision. `review` stores verdict, reviewed revision and reviewing run ID.
`publication` is null when not required; otherwise retain the authorized target,
public-safe deduplication key, intended content/revision, and confirmed receipt.
An artifact records its question, findings and evidence classes, sources/revisions,
contradictions, decision and limitations; it does not need a separate template.

## Blockers and recovery

<For each affected unit: failed condition, evidence, confirmed partial effects,
unblock trigger, next check and exact recovery action. Empty when nothing is blocked.
Do not clear a claim until prior effects and writer exclusion are established.>

## Change log

<Append run ID/time, unit, meaningful change and reason, exact output/review or
publication reference, and next action. Record inconclusive and no-work results
honestly. Keep current state small; archive old history inside the project folder
only after readback and retain a stable pointer. Never discard its only durable copy.>
