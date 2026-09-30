# Paul's Second Brain — Vision, Requirements, Architecture, and Operating Principles


---
type: specification
name: second-brain
date: 2026-09-07
owner: Paul Myers
purpose: Load at the start of a new knowledge base (KB). 
---



# 1. Purpose

This document defines Paul's personal **Second Brain**: a durable personal knowledge system centered on Obsidian and used primarily through conversational AI.

AI can be Claude or ChatGPT, or some future AI.

The goal is not merely to make Obsidian searchable.

The goal is for AI to function as an intelligent partner that can reason across Paul's life: plans, commitments, people, correspondence, calendar, documents, ideas, decisions, goals, work, travel, faith, healthcare, finances, and other durable knowledge.

The intended experience should feel simple:

> Paul talks to AI chat. AI figures out where to look, reasons across the available information, and helps Paul understand what matters.

The underlying system may contain sophisticated metadata, provenance, schemas, retrieval techniques, and AI reasoning, but **Paul should not have to operate that machinery manually**.

The system exists to reduce cognitive load, not create it.

---

# 2. Fundamental Design Principle

## Complexity belongs underneath the system, not in Paul's experience of it.

Paul strongly prefers simple systems and can become overwhelmed by elaborate information architectures, deep taxonomies, excessive categorization, and systems requiring continual maintenance.

This is therefore a hard architectural constraint.

However, simplicity does **not** mean deliberately making the system stupid.

Paul is willing to accept approximately:

- 25% more setup/complexity for roughly 20% more useful capability.
- Up to approximately 50% additional complexity when the resulting capability is genuinely substantial.

Beyond that, complexity has an extremely high burden of proof.

The system should aggressively exploit AI so that **software absorbs complexity instead of transferring it to Paul**.

---

# 3. The Core Model

The Second Brain has two principal components.

## Obsidian = Durable Knowledge

Obsidian is the authoritative durable knowledge layer.

It contains Paul's current durable:

- facts
- decisions
- intentions
- plans
- preferences
- commitments
- knowledge
- understanding
- conclusions
- notes
- todos
- research
- summaries
- journal entries
- important relationship context

Obsidian is the **source of truth for durable meaning**.

It is authoritative, but not infallible.

If newer credible evidence from another system contradicts something in Obsidian, AI should identify the contradiction rather than blindly trusting either source.

AI may recommend how to reconcile the conflict.

AI must never silently overwrite Obsidian.

---

## AI = Intelligence Layer

AI is the primary conversational interface to the Second Brain.

Paul should generally not have to think:

> Which application contains this?

He should be able to ask:

> What are my plans for October?

AI should determine which relevant sources to consult and synthesize the answer.

The desired behavior is not merely retrieval.

AI should reason.

For example, it might discover:

- an October trip described in Obsidian
- airline reservations in Gmail
- calendar events that conflict with the trip
- a todo related to the trip
- an unresolved decision about lodging
- a person Paul intended to visit
- a document related to the trip in OneDrive

The resulting answer should describe the **situation**, not dump search results.

---

# 4. Source-of-Truth Model

Different systems own different kinds of information.

There should NOT be an attempt to force every system into one identical organizational structure.

AI should absorb the heterogeneity.

## Obsidian

Source of truth for:

**Durable meaning.**

Examples:

- Paul's understanding of something
- decisions
- plans
- intentions
- preferences
- important facts
- conclusions
- todos
- durable knowledge
- relationship context
- summaries
- research notes

## Gmail

Source of truth for:

**Original correspondence.**

Gmail can remain largely unstructured.

Paul dislikes organizing email and should not be required to maintain elaborate Gmail folders or labels for the benefit of the Second Brain.

AI should bear the burden of:

- searching Gmail
- finding correspondence
- interpreting it
- connecting it to other information

Important durable meaning discovered in email can be promoted into Obsidian.

The original email remains the evidence.

**Exception:** Some Gmail folders are structured and should be treated as authoritative rather than searched incidentally. Currently:

- **Taxes**, with subfolders per year. When a question concerns tax documents, AI should look here first rather than searching broadly.

Paul will identify additional structured folders over time; this list should be updated as they come up.

## Google Calendar

Source of truth for:

**Scheduled time.**

Examples:

- dates
- times
- locations
- attendees
- appointments
- scheduled events

An event being on Calendar does **not** mean it needs an Obsidian note.

Obsidian should contain the broader durable meaning only when useful.

Example:

Calendar:

> Flight to Rome — October 12, 6:40 PM

Obsidian:

> Italy trip with daughters; purpose, itinerary, decisions, intentions, research, unresolved issues.

## OneDrive

Source of truth for:

**Documents and artifacts.**

Examples:

- PDFs
- Word documents
- Excel spreadsheets
- scans
- statements
- signed documents
- forms
- receipts
- official records

Obsidian stores the meaning.

OneDrive stores the artifact.

## Apple Photos / iCloud

Source of truth for:

**Photos and videos.**

Photos should not routinely be duplicated into OneDrive or Obsidian.

An individual photo may be referenced or incorporated into a note when there is a specific useful reason.

Apple Photos integration with AI is a desired capability, but lack of direct integration should not complicate the initial architecture.

## Apple Contacts

Source of truth for:

**Contact records.**

Examples:

- phone numbers
- email addresses
- addresses
- basic contact information

Obsidian Person notes contain durable knowledge *about* important people.

Apple Contacts contains the contact record itself.

Direct Apple Contacts integration with AI is desirable but is not required for the initial system if achieving it requires substantial complexity.

---

# 5. Provenance

Provenance is a major requirement.

It is not unnecessary complexity.

For Paul, provenance **reduces anxiety** because important claims can be traced back to their evidence.

The guiding principle is:

> Durable meaning in Obsidian should remain reproducibly traceable to the evidence from which it came.

Example:

Obsidian:

> Retirement adviser recommends retiring January 2027.

Possible provenance trail:

    Obsidian statement
        ↓
    OneDrive adviser PDF
        ↓
    Gmail message that delivered the PDF

Where practical, provenance should reach all the way back to the original evidence.

---

# 6. Fine-Grained Provenance

Provenance should ideally be associated with the particular statement or section it supports rather than merely attaching a large list of sources to the entire note.

Example:

```markdown
Retirement eligibility begins January 2027.
<!-- source: OneDrive/.../RetirementAnalysis.pdf -->
```

The precise technical representation may evolve.

The important requirement is conceptual:

> Paul should be able to ask AI Chat, "How do we know that?" and AI should be able to trace the claim back to evidence.

Provenance machinery should be as unobtrusive and machine-maintained as possible.

---

# 7. Documentary Evidence vs AI Reasoning

The system must distinguish between:

1. information supported by documentary evidence
2. conclusions Paul and AI reasoned out together

AI must never manufacture documentary provenance for an inference.

For example:

> Paul's adviser explicitly recommended X.

may have documentary provenance.

Whereas:

> Based on Paul's finances and goals, retiring in January appears reasonable.

is a conclusion.

Both can be valuable.

They are epistemically different.

---

# 8. Epistemic Classification — Considered and Rejected

Systematic epistemic classification means explicitly labeling information according to how it is known.

Possible categories could include:

- fact
- decision
- intention
- inference
- belief
- possibility
- uncertainty
- prediction

A sophisticated implementation might contain metadata such as:

```yaml
epistemic_type: inference
confidence: medium
status: provisional
```

Potential benefits include:

- distinguishing evidence from inference
- machine reasoning over certainty
- identifying uncertain claims
- preventing assumptions from becoming facts

However, systematic epistemic classification was **deliberately rejected for the everyday Second Brain**.

The additional machinery is not currently justified.

Instead, AI should infer these distinctions from ordinary human-readable language.

For example:

> I decided to visit Egypt.

is clearly a decision.

> I'm thinking about visiting Egypt.

is clearly a possibility.

> I believe this happened in 1987.

expresses uncertainty.

No additional schema is necessary unless a real recurring problem demonstrates that it would provide meaningful value.

This is an important architectural principle:

> Do not encode something structurally merely because it can be encoded.

Structure must earn its complexity.

The epistemic-classification decision itself should be documented in the Meta-Brain because it illustrates an important knowledge-management tradeoff.

This differs from provenance.

**Provenance was accepted because its practical and emotional value clearly justifies its complexity.**

---

# 9. Information-Load Firewall

AI should function as an **information-load firewall**.

The system should:

**Search broadly.**

**Reason aggressively.**

**Surface selectively.**

**Store selectively.**

The fact that AI *can* discover something does not mean Paul needs to see it.

The fact that something exists does not mean it belongs in Obsidian.

The fact that information could be categorized does not mean another category should be created.

The purpose of the Second Brain is not maximum information capture.

It is maximum **useful understanding with minimum cognitive burden**.

---

# 10. Selective Capture

Information should be promoted into Obsidian when future Paul is reasonably likely to benefit from having it available as durable knowledge.

Examples include:

- important facts
- decisions
- intentions
- preferences
- commitments
- lessons
- ongoing situations
- significant relationships
- important research conclusions
- plans likely to matter later

Ordinary details should generally remain in their original systems.

AI should be proactive about recommending useful durable capture.

But AI should not turn Paul's life into an exhaustively documented database.

---

# 11. Current Truth Over Historical Accumulation

The Second Brain should strongly favor **current truth**.

When information becomes obsolete, the preferred behavior is usually to update the authoritative existing note rather than accumulate layer after layer of outdated information.

Historical information should be retained when history itself is useful.

Otherwise:

> Current understanding beats exhaustive history.

Paul explicitly wants to avoid a knowledge base becoming a dense forest of old information and tangled relationships.

---

# 12. Update Before Creating

This is one of the strongest organizational rules.

> **Update an existing note before creating another note whenever reasonably possible.**

Before AI recommends creating a new document, it should consider whether the information belongs in an existing authoritative note.

The preferred Second Brain consists of a relatively small number of useful, living documents rather than thousands of fragmented notes.

---

# 13. Permission and Anti-Drift Rules

AI may proactively:

- read
- search
- analyze
- reason
- compare sources
- identify contradictions
- identify stale information
- suggest changes
- suggest new durable knowledge
- suggest cleanup

But:

> **AI must never modify an Obsidian Markdown file without Paul's explicit permission.**

This is a hard rule.

The same general rule applies to external systems.

AI, such as Claude or ChatGPT, may proactively read and reason about:

- Gmail
- Calendar
- OneDrive
- Contacts
- other connected sources

But external state changes require permission.

Examples:

- sending email
- modifying Calendar
- changing Markdown
- moving documents
- editing source files

Permission should be lightweight.

AI does not need to generate elaborate diffs or previews unless Paul asks.

A simple request is sufficient:

> This belongs in your Italy note. Want me to update it?

Permission for one action is not blanket permission for future actions.

## Update Classification (Anti-Drift Guardrail)

To keep the judgment behind "ask before modifying" consistent over time rather than re-derived fresh each session, AI sorts every potential change into one of three buckets:

1. **Silent update** — refining or correcting something already in a note, with no conflict (a date, a detail, a status change).
2. **Ask first** — a new person, project, or decision; or anything that contradicts what's already written.
3. **Don't store** — a one-off mention or passing thought that isn't yet a decision or commitment.

This is a standing behavioral rule, not a new schema. It adds no YAML, no per-note metadata, and nothing for Paul to maintain. If AI misjudges a bucket, Paul should say so in the moment; if misjudgment keeps recurring, that's the signal to consider a more formal mechanism (e.g. a deterministic classification rule, or an append-only change log) rather than relying on this lightweight version.

---

# 14. Second-Brain Mode

The desired conversational behavior is called:

# Second-Brain Mode

In Second-Brain Mode, AI should actively look for useful relationships among available information.

Examples:

- contradictions
- forgotten commitments
- unresolved plans
- opportunities
- conflicts
- stale knowledge
- important changes
- relevant people
- missing follow-up
- goals not reflected in actual behavior

However, Second-Brain Mode is **synchronous**.

It does not require:

- background daemons
- filesystem watchers
- notification infrastructure
- continuous monitoring
- scheduled agents

AI performs this reasoning while Paul is actively interacting with it.

This dramatically reduces architectural complexity.

---

# 15. Example Second-Brain Questions

The system should eventually handle questions such as:

### Planning

> What are my plans for October?

> What am I forgetting about the Egypt trip?

> What travel decisions have I made but haven't acted on?

### Commitments

> What have I promised people recently?

> Is there anything in my email that should be on my todo list?

> What commitments aren't reflected in my calendar?

### People

> Give me a briefing on Madi before the discussion group.

> What was the last thing I discussed with Shruti about this project?

> When did I last communicate with this person and what did we decide?

### Decisions

> What did I decide about retirement?

> Why did I make that decision?

> What evidence was it based on?

### Contradictions

> Is anything in my Second Brain inconsistent with recent email?

> Do my current travel plans conflict with anything?

### Reflection

> What has changed in my life recently?

> What am I worrying about repeatedly?

> What important decisions seem unresolved?

### Retrieval

> Find that thing I wrote about capitalism and socialism.

> What did I learn about Sora?

### Knowledge maintenance

> Is NOW getting cluttered?

> What information should I promote from temporary notes into permanent knowledge?

### Goal alignment

> Does my calendar reflect what I say is important to me?

This last category illustrates why the system is a **Second Brain rather than merely document search**.

---

# 16. Organizational Philosophy

Organization should be understandable without AI.

The test is:

> Would Paul still understand this structure if AI, like Claude or ChatGPT disappeared tomorrow?

AI should compensate for imperfect organization.

Paul should not reorganize his thinking for the convenience of AI.

---

# 17. Top-Level Obsidian Structure

The provisional top-level taxonomy is:

```text
NOW/
ADMIN/
LIFE/
PEOPLE/
CAREER/
HEALTHCARE/
```

These categories should be treated as stable infrastructure.

Folder changes require a **high burden of proof**.

AI, such as Claude or ChatGPT should not recommend new folders merely because:

- a folder contains many notes
- several notes share a topic
- another taxonomy would be theoretically cleaner

Structural changes should be recommended only when actual use demonstrates a meaningful information-architecture problem.

---

# 18. NOW

`NOW` is the system's pressure valve.

It can contain:

- unresolved material
- temporary notes
- active information
- information awaiting filing
- ephemera
- current todos
- uncertain material

It is allowed to be somewhat messy.

When in doubt:

> Put it in NOW.

AI, such as Claude or ChatGPT should function as a **proactive but permissioned NOW gardener**.

It may notice:

- stale material
- notes that obviously belong elsewhere
- temporary material that has become durable
- obsolete notes
- duplicates

AI should suggest cleanup in **small cognitively manageable amounts**.

It should never present Paul with a giant cleanup backlog unless explicitly requested.

---

# 19. Todos

Obsidian remains the source of truth for todos.

Permanent todo notes:

```text
NOW/MyTodos.md
NOW/TrpTodos.md
```

There should not be a separate task-management system unless a demonstrated need eventually justifies one.

AI should reason across:

- todos
- Calendar
- Gmail
- plans
- commitments

For example, AI may notice an email commitment that has not become a todo.

Changes to todo files still require permission.

---

# 20. ADMIN

Likely areas include:

```text
ADMIN/
    Admin/
    Auto/
    Documents/
    Financial/
    Taxes/
    House/
    Insurance/
    Retirement/
```

Taxes may naturally contain year folders:

```text
Taxes/
    2025/
    2026/
```

No top-level Archive is required.

---

# 21. LIFE

Likely areas include:

```text
LIFE/
    Mind/
    Journal/
    Travel/
    Faith/
    Books/
    Words/
```

Earlier concepts such as `Family` and `Friends` need not be used for Person entities now that PEOPLE exists.

Information about family or friends may still naturally appear in LIFE notes when the subject is a life topic rather than a person record.

---

# 22. PEOPLE

PEOPLE is a first-class top-level category.

It should be **flat**.

Examples:

```text
PEOPLE/
    Julia Myers.md
    Anna Myers.md
    Eleanor Myers.md
    Minter.md
    Shruti.md
    Greg.md
```

Do not create subfolders such as:

```text
Family/
Friends/
Work/
Doctors/
```

Relationship type can be represented in metadata.

Person notes should be selective.

Do not create a Person note merely because somebody appears in an email.

A Person note is appropriate for people with meaningful or ongoing relevance.

---

# 23. CAREER

Likely areas include:

```text
CAREER/
    TRP/
    AI/
    Career Development/
    Learning/
```

TRP may contain major durable work domains.

Example:

```text
TRP/
    AEMaaCS Migration/
```

Substructure should be added only when actually useful.

---

# 24. HEALTHCARE

Healthcare information belongs under:

```text
HEALTHCARE/
```

The organization can be person-oriented or topic-oriented where natural.

Healthcare providers who are significant ongoing relationships may have Person notes under PEOPLE while healthcare records and medical knowledge remain under HEALTHCARE.

Do not duplicate the same information simply to satisfy both taxonomies.

---

# 25. One-Home Bias

Information should generally have **one natural home**.

When something could belong in several places:

> Put it where Paul would most naturally look for it later.

Do not duplicate information merely to represent every possible classification.

A useful distinction is:

> Information gets one home. Ideas can have many relationships.

---

# 26. Links

AI does not need extensive wikilinks to understand relationships.

Modern AI can infer semantic relationships dynamically.

Therefore wikilinks should be:

**Sparse and human-useful.**

Use a link when it makes the note more useful to Paul.

Do not create links merely to construct an AI knowledge graph.

A good test:

> Would this link still be useful if AI disappeared tomorrow?

If not, it probably does not belong.

Because a wikilink changes a Markdown file, AI must ask permission before adding one.

---

# 27. Tags

Use a **small controlled vocabulary**.

Tags are a cross-cutting aid, not a second taxonomy.

A tag must earn its existence.

Do not use tags merely to repeat information already represented by:

- folder
- filename
- note type
- YAML metadata

Avoid tag proliferation such as:

```text
#trip
#travel
#planning
#italy
#vacation
#active
```

when those concepts are already obvious from structure or metadata.

---

# 28. YAML / Frontmatter

Unlike visible taxonomy, machine-oriented metadata may be sophisticated.

Paul explicitly welcomes rich YAML because:

1. AI can maintain it.
2. It can increase machine reasoning capability.
3. Paul has professional interest in AI and knowledge management.
4. The metadata itself can become an object of study in the Meta-Brain.

The principle is:

> Schema richness may be complex. Using the Second Brain must not be complex.

Human-facing Markdown remains readable.

Machine-facing metadata can be richer.

---

# 29. Typed Schemas

Different note types may have different schemas.

Potential types include:

- Person
- Trip
- Decision
- Project
- Medical
- Research
- Organization
- Place

Example conceptual Person schema:

```yaml
---
type: person
name: Example Person
relationship: friend
created: 2026-09-07
updated: 2026-09-07
---
```

A Trip might contain different fields:

```yaml
---
type: trip
destination: Egypt
status: considering
created: 2026-09-07
updated: 2026-09-07
---
```

These are illustrative rather than final schema definitions.

The actual schemas should evolve through demonstrated use.

---

# 30. Machine-Maintained Dates

Notes should generally contain machine-maintained:

```yaml
created:
updated:
```

Paul should not have to manually maintain these fields.

Human-facing dates should appear when useful.

Journal filenames should include dates.

---

# 31. Naming

File and folder names are for Paul first.

Use:

- ordinary words
- recognizable names
- searchable language
- nouns
- dates when useful

Avoid:

- clever abbreviations
- artificial AI-friendly names
- cryptic classification systems

AI adapts to Paul's vocabulary.

Paul should not adapt his vocabulary to AI.

AI should recommend renaming only when a name is genuinely confusing or misleading.

---

# 32. Depth

Most information should remain approximately **2–3 levels deep**.

Four levels is an approximate maximum rather than a challenge to reach.

Prefer:

> fewer folders with good names

over:

> elaborate hierarchical classification.

Search should compensate for imperfect filing.

---

# 33. Archives

There should be **no top-level Archive**.

Old information normally remains where future Paul would naturally search for it.

A leaf-level Archive may occasionally make sense when material is truly obsolete but still worth retaining.

Archiving should not become a ritual.

---

# 34. Projects

A top-level `PROJECTS` folder was considered.

It was deliberately **deferred**.

Do not create it merely because projects exist.

Example:

An Italy trip can naturally live under:

```text
LIFE/Travel/Italy/
```

If real usage eventually demonstrates that projects cutting across domains create a genuine problem, the question can be reconsidered.

Until then:

> No PROJECTS top-level category.

---

# 35. Journal

Journal filenames should contain dates.

Example:

```text
2026-09-07.md
```

The broader policy for journal material is intentionally **deferred**.

No decision has yet been made about:

- extracting durable insights automatically
- promotion of journal content
- journal provenance
- how aggressively AI should reason over journals
- whether old journal conclusions should influence current truth

Do not invent a policy until Paul revisits this subject.

---

# 36. The Meta-Brain

The system should contain a **Meta-Brain**.

This is a firm requirement.

The exact folder location and detailed structure remain to be determined.

The Meta-Brain documents and studies the Second Brain itself.

It can contain:

- architecture
- schemas
- metadata definitions
- organizing principles
- provenance design
- retrieval approaches
- AI experiments
- evaluations
- architectural decisions
- rejected alternatives
- lessons learned
- knowledge-management experiments
- explanations of why decisions were made

---

# 37. Why the Meta-Brain Matters

The Meta-Brain serves two purposes.

## Operational

It makes the Second Brain:

**Inspectable rather than magical.**

Paul should be able to understand how the system works.

## Professional / Intellectual

Paul works professionally with:

- AI
- software architecture
- knowledge management
- content systems

The Second Brain can therefore become a practical laboratory for learning about those subjects.

This separation is valuable:

> Paul's personal knowledge stays simple.

while:

> technical complexity can live in the Meta-Brain where Paul can explore it when interested.

This distinction is psychologically important as well as technically useful.

The technical machinery becomes something Paul can study rather than something he must constantly operate.

---

# 38. Meta-Brain and Architectural Decisions

Important tradeoffs should be documented.

Examples:

- why provenance was adopted
- why systematic epistemic classification was rejected
- why links are sparse
- why PEOPLE is flat
- why Gmail remains unstructured
- why current truth is favored
- why PROJECTS was deferred
- why external writes require permission

This creates an evolving architectural record.

---

# 39. Desired Source Universe

The desired Second Brain information universe includes:

```text
Obsidian
Gmail
Google Calendar
OneDrive
Apple Photos
Apple Contacts
Current web information
```

Not every source must have perfect technical integration on day one.

Missing integrations should be treated as **explicit limitations**, not excuses to introduce disproportionate architectural complexity.

---

# 40. Desktop-First Decision

The original vision required the complete experience across:

- Mac
- browser
- iPhone
- iPad

Investigation showed that persistent local filesystem access is currently much easier on desktop than mobile.

Paul subsequently made a deliberate scope decision:

> **Build the initial Second Brain for desktop use only.**

iPhone and iPad parity is deferred.

This is a scope reduction, not a change in the long-term vision.

The system should avoid architectural decisions that unnecessarily prevent future mobile support.

---

# 41. Obsidian Sync

Paul already pays for and uses Obsidian Sync.

The vault therefore already exists on:

- macOS
- iPhone
- iPad

Obsidian Sync should remain responsible for synchronization.

Do **not** introduce another synchronization mechanism without a compelling reason.

In particular, the Second Brain should not require:

- GitHub as a vault transport
- Dropbox as a vault transport
- duplicate cloud knowledge bases
- custom synchronization scripts

simply to give AI access to information that already exists locally.

---

# 42. Preferred Desktop Architecture

The preferred architecture is intentionally boring:

```text
                    Obsidian
                       │
                       │
                Markdown Vault
                       │
                 Obsidian Sync
                       │
                       ▼
              Local Mac Filesystem
                       │
                       ▼
                       AI
```

AI Chat should interact as directly as practical with the local Markdown vault.

The ideal mental model is:

> To AI, Obsidian is just a folder full of Markdown files.

That simplicity is a feature.

---

# 43. ChatGPT Work / Local Folder Access

Research identified ChatGPT's desktop **Work** capability as a promising mechanism for local-folder access.

The intended architecture is:

```text
Obsidian Vault
      │
      ▼
ChatGPT Work
      │
      ├── read Markdown
      ├── reason across notes
      └── modify only after approval
```

However, during setup Paul did **not see Work** in his current desktop application.

Therefore this mechanism has **not yet been validated on Paul's actual account/client**.

This distinction is important.

The architecture should not claim that Work is functioning until it has been experimentally confirmed.

---

# 44. Architecture Alternatives Considered

Several alternatives were investigated.

## Kiro + Obsidian MCP

Advantages:

- direct Markdown access
- good MCP support
- powerful
- Paul already knows Kiro professionally

Rejected as the primary Second-Brain interface because:

- AI should be the interface
- Kiro would create another interaction surface
- it weakens the desired conversational experience

Kiro may still be useful as a **Meta-Brain laboratory or engineering tool**.

## Custom MCP

Advantages:

- potentially direct Obsidian integration
- powerful read/write capability
- architecturally elegant

Disadvantages:

- product/plan limitations
- additional infrastructure
- servers/tunnels/configuration
- mobile limitations
- greater maintenance burden

Rejected for initial implementation.

Reconsider only if native/local access proves inadequate and MCP capability materially improves.

## GitHub Mirror

Concept:

```text
Obsidian
   ↓
Private GitHub repository
   ↓
ChatGPT
```

Advantages:

- excellent Markdown support
- version history
- provenance benefits
- AI-friendly
- familiar engineering technology

Rejected for initial implementation.

Reason:

**Obsidian Sync already synchronizes the vault.**

Adding GitHub merely to transport Markdown to AI creates an unnecessary second synchronization architecture.

Git itself may eventually be useful for versioning or Meta-Brain experimentation, but it should not be introduced merely as plumbing.

## Dropbox Mirror

Concept:

```text
Obsidian
   ↓
Dropbox copy
   ↓
ChatGPT
```

Potentially simple, but rejected for the same basic reason.

It creates a duplicate knowledge copy to compensate for an access problem rather than solving the access problem directly.

## OneDrive Mirror

Rejected as the Obsidian transport mechanism.

OneDrive already has a clear role:

**source-of-truth storage for documents and artifacts.**

It should not acquire a second unrelated responsibility unless necessary.

## Custom Hosted Second-Brain Service

Potentially extremely capable.

Also exactly the sort of architecture this project is trying to avoid.

Rejected for v1 because it introduces:

- hosting
- APIs
- authentication
- maintenance
- synchronization
- security responsibility
- operational burden

Only reconsider if simpler approaches demonstrably fail.

---

# 45. Architectural Principle Learned from the Alternatives

A critical lesson emerged during architecture research:

> Do not build infrastructure to solve a problem the underlying systems have already solved.

Obsidian Sync already solves synchronization.

Therefore the remaining problem is not:

> How do we synchronize Paul's knowledge?

It is:

> How does AI get controlled access to the local synchronized Markdown folder?

That is a much smaller problem.

The architecture should remain focused on that problem.

---

# 46. Freshness Requirement

Real-time synchronization is unnecessary.

**Daily freshness is sufficient.**

An explicit refresh mechanism could eventually exist for unusual situations requiring immediate updates.

Do not pay a significant complexity cost to achieve second-by-second freshness.

---

# 47. Privacy

Cloud AI processing of personal material is acceptable provided that:

- reputable services are used
- sensible security practices are followed
- information is not unnecessarily exposed publicly

There is no requirement for an entirely local/offline AI architecture.

Privacy matters, but a local-only architecture is not required.

---

# 48. Voice

Voice would be useful.

Example:

Paul walking Tank:

> AI, what did I decide about the Italy trip?

However:

**Voice is a nice-to-have, not an architectural driver.**

Do not add significant complexity merely to support voice.

If voice works well with the eventual architecture, use it.

If it is awkward, unreliable, or requires substantial additional machinery, defer it.

---

# 49. Background Processing

The system does not need to constantly monitor Paul's life.

No requirement exists for:

- filesystem watchers
- constant email monitoring
- continuous calendar monitoring
- background agents
- event-driven pipelines

Second-Brain intelligence happens primarily when Paul asks AI Chat something.

This is another important simplification.

---

# 50. Contradiction Handling

Obsidian is authoritative but not infallible.

Suppose Obsidian says:

> Trip begins October 12.

but a newer airline email says:

> Flight changed to October 13.

AI should not silently choose one.

It should say, in substance:

> Your Italy note says October 12, but the newer airline confirmation says October 13. The airline email appears to be newer. I think the Obsidian note is stale. Want me to update it?

AI may provide up to approximately three plausible resolutions when ambiguity genuinely exists.

Avoid overwhelming Paul with large decision trees.

---

# 51. Source Reconciliation

A useful conceptual model is:

```text
Obsidian
    intended/current durable truth

Calendar
    scheduled reality

Gmail
    correspondence and evidence

OneDrive
    documentary artifacts

Apple Contacts
    contact records

Apple Photos
    visual record
```

AI's job is to reconcile these into an understandable picture.

---

# 52. Proactive Reasoning Examples

Second-Brain Mode should eventually support useful behaviors such as:

## Open-Loops Review

Identify things Paul intended to do but has not apparently completed.

## Commitment Detection

Notice commitments made in email that do not appear in todos or Calendar.

## Goal-to-Calendar Alignment

Compare stated goals with scheduled time.

## Relationship Briefings

Before interacting with an important person, synthesize:

- Person note
- recent correspondence
- relevant Calendar events
- unresolved commitments

## Travel Readiness

Combine:

- trip note
- reservations
- Calendar
- correspondence
- todos
- documents

and identify missing pieces.

## Contradiction Detection

Identify outdated durable knowledge when newer evidence exists.

## NOW Gardening

Suggest a small number of useful cleanup actions.

## Durable-Knowledge Suggestions

After an important AI Chat conversation:

> We made two decisions here that seem worth preserving in Obsidian. Want me to add them?

## Provenance Explanation

Answer:

> Where did that come from?

with the evidence trail.

## "What Am I Forgetting?"

Search across the relevant systems for commitments, unresolved decisions, and plans.

These capabilities are the heart of the Second Brain.

---

# 53. Maintenance Philosophy

Maintenance should be minimal.

Paul should not routinely have to:

- groom metadata
- maintain links
- reorganize folders
- classify notes
- clean email
- reconcile databases
- maintain synchronization scripts

AI should perform or recommend machine-oriented maintenance wherever possible.

Human attention should be reserved for **meaningful decisions**.

---

# 54. Failure Behavior

When AI cannot access a required source, it should say so.

It must never pretend to have searched something it could not search.

Example:

> I checked Obsidian and Calendar. I couldn't access Gmail for this query, so this may be incomplete.

This is preferable to confident hallucination.

---

# 55. Search Before Structure

When information is difficult to find, the first response should generally be:

> Improve retrieval.

not:

> Add more taxonomy.

AI search substantially reduces the need for elaborate filing systems.

Structure should exist where it improves human comprehension and durable knowledge management.

---

# 56. Human-First / Machine-Rich

The system intentionally combines two seemingly opposite principles:

## Human-facing structure should be simple.

Folders, filenames, Markdown, and organization should remain understandable.

## Machine-facing structure can be rich.

YAML, schemas, provenance, timestamps, and other metadata can be sophisticated when they materially improve AI capability.

AI, whether it is ChatGPT, Claude, Gemini, or some other model should maintain the machine-facing layer so Paul does not have to.

---

# 57. Success Criteria

The Second Brain is successful when Paul can sit at his Mac and ask the AI Chat Bot ordinary questions about his life without thinking about information architecture.

Examples:

> What are my plans for October?

> What did I decide about retirement?

> What am I forgetting?

> Find the evidence for that.

> What's unresolved with this trip?

> What should I know before meeting this person?

> Did I promise somebody something that I haven't done?

And AI can intelligently consult the relevant information.

The system should feel like:

**one conversation over Paul's life**

rather than:

**a collection of databases Paul must manually query.**

---

# 58. Anti-Success Criteria

The system has failed if Paul regularly has to think about:

- synchronization
- MCP servers
- repositories
- embeddings
- indexes
- metadata maintenance
- elaborate folder taxonomies
- pipelines
- connectors
- duplicate databases
- agent infrastructure

Those technologies may occasionally exist underneath the system. And since Paul has an interest in AI foundations and especially MCP connectors for his job, AI can suggest or recommend new features or capabilities.

They must not become Paul's job.

---

# 59. Implementation Strategy

Implementation should proceed incrementally.

The first milestone is intentionally tiny:

> **Can AI reliably reason across Paul's local Obsidian Markdown on the Mac?**

Test using a safe test area rather than the real vault.

Existing test material includes fictional Markdown notes containing known retrieval markers such as:

- `PURPLE WALRUS`
- `BLUE PELICAN`

These are test data only.

They must never be interpreted as facts about Paul.

Once reliable read access works, test:

1. exact retrieval
2. semantic retrieval
3. cross-note reasoning
4. YAML understanding
5. provenance
6. contradiction detection

Only after those work should write behavior be tested.

And even then:

> **No write without Paul's explicit approval.**

---

# 60. Implementation Order

Preferred sequence:

```text
1. Establish simple local Obsidian read access on Mac.

2. Validate retrieval against test notes.

3. Validate cross-note reasoning.

4. Validate permissioned Markdown updates.

5. Add/validate Gmail reasoning.

6. Add/validate Google Calendar reasoning.

7. Add/validate OneDrive document retrieval/provenance.

8. Establish typed YAML schemas gradually.

9. Establish provenance conventions.

10. Build the Meta-Brain documentation.

11. Test real Second-Brain workflows.

12. Revisit Apple Contacts and Photos when useful integration exists.

13. Revisit mobile access later.
```

Do not attempt all thirteen simultaneously.

---

# 61. Rule for Future Architecture Changes

Any proposed new technology should answer four questions:

1. What actual problem does it solve?
2. How much useful capability does it add?
3. How much setup and ongoing maintenance does it introduce?
4. Can AI absorb that complexity instead of Paul?

If the answers are weak:

> Don't add it.

---

# 62. Final Operating Principles

The Second Brain should obey these principles:

1. **Obsidian is the durable knowledge source of truth.**
2. **AI is the primary intelligence and conversational interface.**
3. **Obsidian stores meaning; source systems store artifacts/evidence.**
4. **Preserve reproducible provenance for important durable knowledge.**
5. **Search broadly, reason aggressively, surface selectively.**
6. **Store selectively.**
7. **Prefer current truth over historical accumulation.**
8. **Update existing notes before creating new ones.**
9. **Information normally gets one home.**
10. **Links are sparse and human-useful.**
11. **Tags use a small controlled vocabulary and must earn their existence.**
12. **Human-facing structure stays simple.**
13. **Machine-facing metadata may be rich.**
14. **Paul should not maintain machinery that AI can maintain.**
15. AI may proactively read and reason.**
16. **AI must ask before modifying external state.**
17. **Obsidian is authoritative but not infallible.**
18. **Contradictions should be surfaced, not silently resolved.**
19. **Gmail can remain messy; AI absorbs the search burden.**
20. **Calendar owns scheduled time.**
21. **OneDrive owns documentary artifacts.**
22. **Apple Photos owns photos and videos.**
23. **Apple Contacts owns contact records.**
24. **NOW is a pressure valve, not a failure of organization.**
25. **Folder architecture should change rarely.**
26. **Do not add structure merely because structure is possible.**
27. **No top-level PROJECTS unless actual experience proves it necessary.**
28. **Journal policy remains deliberately deferred.**
29. **The Meta-Brain makes the machinery inspectable.**
30. **Second-Brain Mode is proactive but synchronous.**
31. **Voice is optional.**
32. **Desktop is the initial implementation target.**
33. **Obsidian Sync remains the synchronization system.**
34. **Do not create GitHub/Dropbox/cloud mirrors.**
35. **Direct local Markdown access is preferred.**
36. **Never pretend a source was searched when it was unavailable.**
37. **Complexity must earn its place.**
38. **The system exists to reduce Paul's cognitive load.**

---

# 63. North Star

The ultimate experience is simple.

Paul should be able to open an AI Chat Bot and say:

> **What's going on in my life that I should know about?**

And AI should know where to look.

It should understand that Paul's knowledge, correspondence, schedule, documents, people, and plans live in different systems.

It should reconcile them intelligently.

It should notice things Paul might have forgotten.

It should distinguish durable knowledge from evidence.

It should preserve where important information came from.

It should suggest improvements without drowning Paul in them.

It should ask before changing anything.

And underneath all of that sophistication, Paul's durable Second Brain should remain something beautifully ordinary:

> **A comprehensible collection of Markdown files that belongs to Paul.**
