# EndlessZenFramework

A minimal starter for one autonomous researcher in **ChatGPT**, with **GitHub**
as a research source and optional publication surface, and **Google Drive** as
persistent project memory. It contains instructions and templates, not a running
agent, an installer, or a guarantee of uninterrupted execution.

## Set up one researcher

1. Define a narrow research question, intended reader, deliverable and completion
   gates. Name the repositories the worker may access. GitHub is read-only by
   default; publication needs an explicit grant for each repository and action.
2. Connect GitHub and Google Drive in the ChatGPT experience you will actually use.
   Check its available actions and permissions, not just whether an app is connected.
   See the official [app guidance][apps] and [GitHub guidance][github]. A read-only
   connection is enough for repository research, but not for publishing issues or PRs.
3. Create one private Drive project folder. Copy and complete
   [PROJECT_MANIFEST](templates/PROJECT_MANIFEST.md) and
   [STATE_AND_QUEUE](templates/STATE_AND_QUEUE.md) there. Keep their stable file IDs
   in the completed prompt. Create an `Artifacts` subfolder only for the first result.
4. Copy [the researcher prompt](prompts/RESEARCHER.md) into a dedicated chat, replace
   its placeholders, and run one supervised cycle. Authorize a small Drive
   create/update/readback trial inside the project folder. Verify the file's parent
   and contents. Do not assume the same capabilities exist in scheduled runs.
5. Using the completed prompt, request **one** recurring task at an available cadence
   in your timezone. Keep the queue in Drive, not in the task prompt. The first
   scheduled cycle verifies its own access and write ownership before research.
   Mark setup ready only after that evidence is recorded and read back.

Example scheduling request, after completing the private setup:

```text
Run the following researcher instructions once per hour in <IANA timezone>.
Report briefly after every run, including blocked and no-work outcomes.
<PASTE THE COMPLETED RESEARCHER PROMPT HERE>
```

The cadence must be supported by the account. Scheduling and app availability depend
on the selected experience and permissions; some actions may require approval. Read
[the current task documentation][tasks]. Do not rely on chat history or uploaded
project files as the scheduled worker's control state.

## Minimum operating contract

Every wake reads durable state, recovers interrupted work, and performs one bounded
unit: `ORIENT -> SELECT -> CLAIM -> PRODUCE -> VERIFY -> COMMIT`.
Research ends in a supported decision or an explicit inconclusive result. Producing
an answer and accepting it happen in different runs. GitHub facts are read from the
live repository; Drive owns the research queue, evidence and decisions.

Safe writes require verified serialization of **all** entry points, including manual
runs and retries, or enforced conditional ownership covering every affected write.
One timer, a claim field or a revision counter is not a lock. This repository supplies
no lock implementation. Until the selected environment proves safe ownership, keep
writes supervised under verified exclusion, or remain read-only and report the gate.

A worker must not stop its own recurring task because it is blocked, finished or out
of work. The owner manages the schedule and checks for missing run reports; a worker
cannot report a wake that never happened. Provider-side pauses remain possible.

## Keep deployment data private

Only blank templates belong here. Keep filled prompts, Drive URLs and IDs, control
state, research notes, account details, credentials and run history outside this
public repository. Publish only authorized, sanitized findings that a reader can
understand without private sources. Never import another repository's Git history.

The entire starter is this README, the prompt, two control templates, contributor
instructions in [AGENTS.md](AGENTS.md), and the original [MIT license](LICENSE).
There are no bots, product integrations, execution controllers or code dependencies.

[apps]: https://help.openai.com/en/articles/11487775-connectors-in-chatgpt
[github]: https://help.openai.com/en/articles/11145903-connecting-github-to-chatgpt
[tasks]: https://help.openai.com/en/articles/10291617-tasks-in-chatgpt
