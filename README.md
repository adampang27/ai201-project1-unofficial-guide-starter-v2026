# The Unofficial Guide

Adam Pang - `advice_threads`

---

# Unit 1

## What This Does

This answers questions from advice_threads, a set of 23 forum threads containing student replies. I chose to retrieve the specific reply that supports an answer and name its source so I can trace where each answer came from. If the threads do not contain enough information to answer a question, the system refuses rather than filling in the gap.

## Chunking Strategy

**Chunk size:** One reply  
**Overlap:** 0 characters between replies

Each file in advice_threads is one question with three to five replies, and the replies often disagree, so a chunk is one reply with the THREAD: title repeated on it. Overlap is 0 so the end of one reply is not copied onto the next. 

The starter had 800 character windows and 120 characters of overlap which turned 23 threads into 26 chunks, including a 2-character extra.



<!-- What about YOUR documents made you pick these numbers? Short posts and
     long sectioned guides don't want the same chunking, and "800 seemed
     reasonable" earns nothing. Point at something you noticed when you read
     the documents in Milestone 1.

     If you changed your mind partway through, say so and say why. That's worth
     more than pretending you got it right first time.

     Milestone 3. -->

## Sample Chunks

<!-- Five chunks, pasted as text. Label each one and name the file it came from
     AND the function that produced it — the grader checks your code against
     what you claim here.

     `python app.py chunks -n 5` prints all three for you. Copy them straight
     across.

     Milestone 3. -->

**Chunk 1** — source: `thread_bike_commute.txt` — produced by: `chunker.py::split_documents`

```
THREAD: Is a bike worth it for a 20 minute walk commute?

--- reply 1 (14 votes) ---
Yeah. Cuts an 18 minute walk to about 6. The thing nobody mentions is storage — covered bike parking exists at three buildings and is full by 9am at all three.
```

**Chunk 2** — source: `thread_first_gen.txt` — produced by: `chunker.py::split_documents`

```
THREAD: Anything specific for first-generation students?

--- reply 2 (41 votes) ---
The thing I'd say: the unwritten rules are the hard part, not the coursework. Ask about the unwritten rules explicitly. People are happy to explain them and nobody volunteers them.
```

**Chunk 3** — source: `thread_laptop_specs.txt` — produced by: `chunker.py::split_documents`

```
THREAD: How much laptop do I actually need for CS courses?

--- reply 3 (12 votes) ---
I did two years on an 8GB machine and it was fine until the last project, at which point it very much wasn't. 16 is the answer.
```

**Chunk 4** — source: `thread_parking.txt` — produced by: `chunker.py::split_documents`

```
THREAD: Worth getting a parking permit?

--- reply 2 (21 votes) ---
Street parking on Verrill is legal and free and unmarked, which is why half the upper years do it.
```

**Chunk 5** — source: `thread_sleep_schedule.txt` — produced by: `chunker.py::split_documents`

```
THREAD: Everyone says fix your sleep. Does it actually matter?

--- reply 2 (37 votes) ---
The library being open until 2am is a trap. It's a resource, not a schedule.
```

## Sample Answer

**Question:** Where can you go if you need reliable silence to study?

**Answer:** According to the documents, if you need reliable silence, the only place that reliably delivers it is the library's third floor (thread_study_spots.txt).

```
Sources retrieved: thread_pass_fail.txt, thread_study_spots.txt
```

**My relevance cutoff:** 0.6

Questions the corpus covers came back between 0.15 and 0.31. Questions it doesn't cover came back between 0.81 and 0.90. 0.6 sits in that gap, so I left THRESHOLD in config.py at 0.6.

| Question | In corpus? | Best distance |
|---|---|---|
| How awesome is it that the library is open until 2 am? | yes | 0.289 |
| Where can you go if you need reliable silence to study? | yes | 0.283 |
| When are office hours better than sending an email? | yes | 0.307 |
| What can commuters rent in the student centre? | yes | 0.310 |
| When do large employers close summer internship applications? | yes | 0.151 |
| What is the capital of Mongolia? | no | 0.894 |
| How do I change the oil in a diesel engine? | no | 0.896 |
| Who won the 1994 World Cup? | no | 0.893 |
| What is the recommended dosage of ibuprofen for a headache? | no | 0.807 |
| How do I write a for loop in Rust? | no | 0.835 |

## How I Used AI

**1.** I used AI to explore possible ways to chunk the replies, then checked those suggestions against the structure of my own documents. One suggestion was to split on `---` reply and then divide anything over 800 characters into smaller windows. After inspecting the replies and seeing that the longest was only a few hundred characters, I removed the second step because it solved a problem my data did not actually have.

**2.** I used AI to clarify what chunk size and overlap change, then checked whether those choices fit this corpus. The starter’s overlap was creating tiny extra chunks without preserving useful context, so I set it to 0. Each reply is already a complete answer, and carrying text across replies would mix different students’ advice.

<!-- ── Stretch features ─────────────────────────────────────────────────────
     Doing one? Say so here BEFORE you start. A feature this README never
     claims earns nothing.
     ───────────────────────────────────────────────────────────────────────── -->

---

# Unit 2

<!-- These sections get ADDED to what's already above. Don't delete or rewrite
     unit 1 — the point is that someone can see what you said before you knew
     how it went. -->

## Run Log — Before

I ran `python run_eval.py --label before` on September 29 at 23:15.
It asked each of the five questions three times using `advice_threads`,
top-k 5, a cutoff of 0.6, and caching off. The
[results file](results/run_2026-09-29_2315_before.md) was produced by
`run_eval.py::main` and `run_eval.py::write_report`.
There's no `scorer.py` yet, so these scores come from reading the saved answers.

| Criterion | Target | Run 1 | Run 2 | Run 3 | Verdict |
|---|---|---|---|---|---|
| 1. Retrieved chunk contains the answer | 4 of 5 | 5/5 | 5/5 | 5/5 | MET |
| 2. Every answer names a source | 5 of 5 | 5/5 | 5/5 | 5/5 | MET |
| 3. Gate stops out-of-corpus questions | 4 of 5 | 5/5 | 5/5 | 5/5 | MET |
| 4. Chunks are complete replies | 4 of 5 | 5/5 | 5/5 | 5/5 | MET |
| 5. When a thread names more than one place or time, answers include more than one | 4 of 5 | 1/5 | 1/5 | 1/5 | MISSED |

The report saves source names and distances. I also checked the full chunks
in the existing index and saved them in the
[supporting checks](results/before_supporting_checks.md). The sources and
distances matched the report, and all five questions had a chunk with the
answer. Retrieval gives the same results each time, so criterion 1 stays
at 5/5. The gate was tested once, so its 5/5 goes in all three columns.
For criterion 4, I checked the same five Unit 1 samples three times.
Each was a full reply with no sentences cut off.

For criterion 5, I counted answers with two or more places, or two or more
times. Only the internship answer did this, naming October and November,
so the score is 1/5 in each run. My questions mostly ask for one fact.
The silence question even asks for a place the source calls the only
reliable option. Those answers can be correct while naming just one option,
so these questions are a poor fit for testing this criterion.

The scores stayed the same, but the wording changed in most answers.
`run_eval.py::run_once` calls `generate.py::answer_from_chunks` with
`cache=False`, and the run made 15 model calls.

**Criterion 1 — retrieved chunks contain the answer**

These chunks came from `chunker.py::split_documents` and were retrieved
by `store.py::search`. Each contains the answer to its question:

Question: How awesome is it that the library is open until 2 am? Source: `thread_sleep_schedule.txt#1`.

```text
THREAD: Everyone says fix your sleep. Does it actually matter?

--- reply 2 (37 votes) ---
The library being open until 2am is a trap. It's a resource, not a schedule.
```

Question: Where can you go if you need reliable silence to study? Source: `thread_study_spots.txt#2`.

```text
THREAD: Best study spots that aren't the library?

--- reply 3 (14 votes) ---
Depends what you need. If you need silence, the library third floor is the only place that reliably delivers it.
```

Question: When are office hours better than sending an email? Source: `thread_professor_email.txt#1`.

```text
THREAD: Do professors actually answer email?

--- reply 2 (33 votes) ---
Office hours are dramatically more effective than email for anything that takes more than two sentences to answer. They're also usually empty.
```

Question: What can commuters rent in the student centre? Source: `thread_commuting.txt#1`.

```text
THREAD: Commuting an hour each way — is it survivable?

--- reply 2 (21 votes) ---
The commuter lounge in the student centre has lockers you can rent for $20 a year and it changes the experience completely.
```

Question: When do large employers close summer internship applications? Source: `thread_internship_timing.txt#0`.

```text
THREAD: When should I start looking for a summer internship?

--- reply 1 (30 votes) ---
Earlier than feels reasonable. Large employers close applications in October and November for the following summer.
```

**Criterion 2 — every answer names a source**

Run 1 answers from `generate.py::answer_from_chunks`, saved by
`run_eval.py::write_report`. Each names a source:

Question: How awesome is it that the library is open until 2 am?

```text
According to the documents, the library being open until 2am is described as "a trap" and "a resource, not a schedule."

Source: `thread_sleep_schedule.txt`
```

Question: Where can you go if you need reliable silence to study?

```text
According to the documents, if you need reliable silence, the library third floor is the only place that reliably delivers it (thread_study_spots.txt).
```

Question: When are office hours better than sending an email?

```text
Office hours are more effective than email for anything that takes more than two sentences to answer (thread_professor_email.txt).
```

Question: What can commuters rent in the student centre?

```text
Commuters can rent lockers in the student centre for $20 a year (thread_commuting.txt).
```

Question: When do large employers close summer internship applications?

```text
Large employers close applications for summer internships in October and November for the following summer.

Source: thread_internship_timing.txt
```

**Criterion 3 — the gate stops out-of-corpus questions**

Output from `run_eval.py::check_out_of_scope`, which uses `gate.py::check`
with a cutoff of 0.6:

```text
Out-of-scope questions (the gate should refuse these):
  refused  (best distance 0.893)  What is the capital of Mongolia?
  refused  (best distance 0.896)  How do I change the oil in a diesel engine?
  refused  (best distance 0.893)  Who won the 1994 World Cup?
  refused  (best distance 0.807)  What is the recommended dosage of ibuprofen for a headache?
  refused  (best distance 0.835)  How do I write a for loop in Rust?
  -> gate refused 5 of 5
```

**Criterion 4 — chunks are complete replies**

These are the same five samples shown in Unit 1. They came from
`chunker.py::split_documents`, using the sample selection in
`app.py::cmd_chunks` with `-n 5`. Each is one complete reply.
All three checks are saved in the supporting file.

**Chunk 1** — source: `thread_bike_commute.txt#0`; produced by: `chunker.py::split_documents`

```text
THREAD: Is a bike worth it for a 20 minute walk commute?

--- reply 1 (14 votes) ---
Yeah. Cuts an 18 minute walk to about 6. The thing nobody mentions is storage — covered bike parking exists at three buildings and is full by 9am at all three.
```

**Chunk 2** — source: `thread_first_gen.txt#1`; produced by: `chunker.py::split_documents`

```text
THREAD: Anything specific for first-generation students?

--- reply 2 (41 votes) ---
The thing I'd say: the unwritten rules are the hard part, not the coursework. Ask about the unwritten rules explicitly. People are happy to explain them and nobody volunteers them.
```

**Chunk 3** — source: `thread_laptop_specs.txt#2`; produced by: `chunker.py::split_documents`

```text
THREAD: How much laptop do I actually need for CS courses?

--- reply 3 (12 votes) ---
I did two years on an 8GB machine and it was fine until the last project, at which point it very much wasn't. 16 is the answer.
```

**Chunk 4** — source: `thread_parking.txt#1`; produced by: `chunker.py::split_documents`

```text
THREAD: Worth getting a parking permit?

--- reply 2 (21 votes) ---
Street parking on Verrill is legal and free and unmarked, which is why half the upper years do it.
```

**Chunk 5** — source: `thread_sleep_schedule.txt#1`; produced by: `chunker.py::split_documents`

```text
THREAD: Everyone says fix your sleep. Does it actually matter?

--- reply 2 (37 votes) ---
The library being open until 2am is a trap. It's a resource, not a schedule.
```

**Criterion 5 — answers include multiple places or times**

Run 1 answers from `generate.py::answer_from_chunks`, saved by
`run_eval.py::write_report`:

The study answer names one place:

```text
According to the documents, if you need reliable silence, the library third floor is the only place that reliably delivers it (thread_study_spots.txt).
```

The internship answer names two months:

```text
Large employers close applications for summer internships in October and November for the following summer.

Source: thread_internship_timing.txt
```

The other three answers each name fewer than two places or times.
This is the same in all three runs, giving 1/5 each time.

## Verdicts

These verdicts use the original targets in [criteria.md](criteria.md).
Each target has to hold in all three runs.

| # | Criterion | Verdict | How I decided |
|---|---|---|---|
| 1 | Retrieved chunks contain the answer | MET | All five questions had a retrieved chunk with the answer in each run, so 5/5 met the 4/5 target every time. |
| 2 | Every answer names a source | MET | All 15 saved answers named a source file, giving 5/5 in every run against a target of 5/5. |
| 3 | The relevance gate stops out-of-corpus questions | MET | The gate blocked all five out-of-scope questions, so its 5/5 result met the 4/5 target and goes in all three columns. |
| 4 | Chunks are complete replies | MET | All five sampled chunks were complete replies with no sentences cut off in any of the three checks, so 5/5 met the 4/5 target each time. |
| 5 | When a thread names more than one place or time, answers include more than one | MISSED | Only the internship answer included two times, October and November, so each run was 1/5 against the original 4/5 target. |

Criterion 5 needs the closest look. The strongest case for calling it MET
is that the answers cover what the questions ask: the silence question,
for example, asks for a place the source calls the only reliable option.
One place is enough to answer that question. This shows a problem with
using these questions to test multiple options. It still doesn't show
four of five answers meeting the original target, so I kept MISSED.
I haven't revised any criteria or targets.

## Diagnoses

Only criterion 5 missed. The target was 4 of 5 answers including more than
one place or time, and the result was 1/5 in all three runs.

**Stage: generation.** The model chose the one detail that answered each
question, even when the retrieved chunks included other places or times.
This is where the extra options were left out. The prompt in `generate.py`
says, "Be brief. Two or three sentences is usually enough." It does not
ask the model to include multiple relevant options. That fits the short
answers in the results, though the saved runs alone cannot prove that the
briefness instruction caused them.

For example, I asked, "Where can you go if you need reliable silence to
study?" The [saved chunks](results/before_supporting_checks.md) included
the library third floor, library group study rooms, Ridgeway Café before
10am, and lounges in the science building. `generate.py::build_prompt`
passes all of those replies to the model. The
[answer from run 1](results/run_2026-09-29_2315_before.md) was:

```text
According to the documents, if you need reliable silence, the library third floor is the only place that reliably delivers it (thread_study_spots.txt).
```

I checked three possible causes:

1. Loading could have missed the other replies. All four study replies are
   present in the saved chunks, so that does not explain this example.
2. Retrieval could have returned only one place. It returned all four,
   with complete replies, so neither missing results nor cut sentences
   explains the single place in the answer.
3. Generation could have picked only the detail that best matched the
   question. The model had the other replies but named only the third
   floor, which is what the question about reliable silence called for.

The pattern is the same across the four questions counted as misses.
The library answer gives the warning about 2am, the study answer gives
the third floor, the office hours answer gives the two sentence rule,
and the commuter answer gives lockers. Each focuses on one fact in all
three runs. The internship answer names October and November, so it is
the only one that passes the count.

There is a limit to this diagnosis. The study reply calls the third floor
the only place that reliably delivers silence. The other places are not
described as equally reliable for that need. Naming one place can be the
right answer here. The low count comes from narrow questions producing
focused answers, while criterion 5 expects multiple options. The evidence
shows where the count drops, but it does not show four wrong answers or
prove that relevant alternatives were ignored.

## The Improvement

**What I changed:**

**Why I picked it:**

<!-- Connect it to a specific diagnosis above in one sentence. If you can't,
     you picked a fix because it sounded impressive. -->

### Run Log — After

<!-- Same format, same five criteria, three runs each.
     `python run_eval.py --label after` -->

| Criterion | Target | Run 1 | Run 2 | Run 3 | Verdict |
|---|---|---|---|---|---|
| 1. Retrieved chunk contains the answer | 4 of 5 |  |  |  |  |
| 2. Every answer names a source | 5 of 5 |  |  |  |  |
| 3. Gate stops out-of-corpus questions | 4 of 5 |  |  |  |  |
| 4. | | | | | |
| 5. | | | | | |

**Did it help?**

<!-- Say plainly whether it did, and how you know. If it made things worse,
     say that — a change that backfired, honestly reported, earns full credit
     and is more interesting than one that worked. What matters is that you can
     tell.

     Milestone 4. -->

## What's Still Broken

<!-- For each criterion still missed after your fix: what you'd do about it,
     and why you stopped where you did.

     "I ran out of time" is fine if it's true. Pretending nothing is left is
     not.

     Milestone 5. -->

## What I'd Do Differently

<!-- Knowing what you know now — which of your five criteria would you write
     differently, and why?

     Milestone 5. -->
