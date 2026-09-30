# Baseline supporting checks

Supplementary local checks performed after the saved evaluation in
`results/run_2026-09-29_2315_before.md`, using the existing
`advice_threads__default` index without changing the pipeline or making
generation calls. The evaluation report saves answer text and source
filenames, but not the retrieved chunk text, so that text is recorded here.

## Retrieved chunks

Produced by `store.py::search`; chunk text produced by
`chunker.py::split_documents`. Top-k: 5. Relevance cutoff: 0.6.

### How awesome is it that the library is open until 2 am?

**thread_sleep_schedule.txt#1** — distance: 0.2887; produced by: `chunker.py::split_documents`

```text
THREAD: Everyone says fix your sleep. Does it actually matter?

--- reply 2 (37 votes) ---
The library being open until 2am is a trap. It's a resource, not a schedule.
```

**thread_study_spots.txt#0** — distance: 0.5073; produced by: `chunker.py::split_documents`

```text
THREAD: Best study spots that aren't the library?

--- reply 1 (23 votes) ---
Ridgeway Café before 10am. Empty, quiet, good coffee, and they don't push you out.
```

**thread_study_spots.txt#1** — distance: 0.5131; produced by: `chunker.py::split_documents`

```text
THREAD: Best study spots that aren't the library?

--- reply 2 (19 votes) ---
The science building has open lounges on floors 2 through 5 that are unlocked and almost always empty.
```

**thread_study_spots.txt#2** — distance: 0.5321; produced by: `chunker.py::split_documents`

```text
THREAD: Best study spots that aren't the library?

--- reply 3 (14 votes) ---
Depends what you need. If you need silence, the library third floor is the only place that reliably delivers it.
```

**thread_commuting.txt#2** — distance: 0.5480; produced by: `chunker.py::split_documents`

```text
THREAD: Commuting an hour each way — is it survivable?

--- reply 3 (13 votes) ---
Watch the evening bus timetable before you register for anything that ends after 6pm.
```

### Where can you go if you need reliable silence to study?

**thread_study_spots.txt#2** — distance: 0.2834; produced by: `chunker.py::split_documents`

```text
THREAD: Best study spots that aren't the library?

--- reply 3 (14 votes) ---
Depends what you need. If you need silence, the library third floor is the only place that reliably delivers it.
```

**thread_study_spots.txt#3** — distance: 0.5215; produced by: `chunker.py::split_documents`

```text
THREAD: Best study spots that aren't the library?

--- reply 4 (9 votes) ---
The group study rooms in the library can be booked by one person and used alone. Nobody checks.
```

**thread_study_spots.txt#0** — distance: 0.5311; produced by: `chunker.py::split_documents`

```text
THREAD: Best study spots that aren't the library?

--- reply 1 (23 votes) ---
Ridgeway Café before 10am. Empty, quiet, good coffee, and they don't push you out.
```

**thread_study_spots.txt#1** — distance: 0.6213; produced by: `chunker.py::split_documents`

```text
THREAD: Best study spots that aren't the library?

--- reply 2 (19 votes) ---
The science building has open lounges on floors 2 through 5 that are unlocked and almost always empty.
```

**thread_pass_fail.txt#0** — distance: 0.6584; produced by: `chunker.py::split_documents`

```text
THREAD: When should you actually use the pass/fail option?

--- reply 1 (24 votes) ---
For a course outside your major that you're taking because you're curious. That's what it's for and most people never use it.
```

### When are office hours better than sending an email?

**thread_professor_email.txt#1** — distance: 0.3065; produced by: `chunker.py::split_documents`

```text
THREAD: Do professors actually answer email?

--- reply 2 (33 votes) ---
Office hours are dramatically more effective than email for anything that takes more than two sentences to answer. They're also usually empty.
```

**thread_professor_email.txt#2** — distance: 0.4938; produced by: `chunker.py::split_documents`

```text
THREAD: Do professors actually answer email?

--- reply 3 (15 votes) ---
Empty office hours is the biggest unused resource here and I say that having wasted a year not going.
```

**thread_professor_email.txt#0** — distance: 0.5742; produced by: `chunker.py::split_documents`

```text
THREAD: Do professors actually answer email?

--- reply 1 (21 votes) ---
Varies enormously. General rule I've found: if the syllabus states a response window, it's honoured. If it doesn't, assume 48 hours and don't panic before then.
```

**thread_office_hours_etiquette.txt#1** — distance: 0.5939; produced by: `chunker.py::split_documents`

```text
THREAD: Is it weird to go to office hours with no specific question?

--- reply 2 (29 votes) ---
They're usually empty. You are doing the instructor a favour by turning up.
```

**thread_office_hours_etiquette.txt#2** — distance: 0.6386; produced by: `chunker.py::split_documents`

```text
THREAD: Is it weird to go to office hours with no specific question?

--- reply 3 (18 votes) ---
If it helps, treat it as a standing appointment. Go every week for a month and it stops feeling like a thing.
```

### What can commuters rent in the student centre?

**thread_commuting.txt#1** — distance: 0.3099; produced by: `chunker.py::split_documents`

```text
THREAD: Commuting an hour each way — is it survivable?

--- reply 2 (21 votes) ---
The commuter lounge in the student centre has lockers you can rent for $20 a year and it changes the experience completely.
```

**thread_study_spots.txt#3** — distance: 0.5542; produced by: `chunker.py::split_documents`

```text
THREAD: Best study spots that aren't the library?

--- reply 4 (9 votes) ---
The group study rooms in the library can be booked by one person and used alone. Nobody checks.
```

**thread_bike_commute.txt#3** — distance: 0.5778; produced by: `chunker.py::split_documents`

```text
THREAD: Is a bike worth it for a 20 minute walk commute?

--- reply 4 (5 votes) ---
If you do get one, the campus does free registration and it's the only reason I got mine back after it was taken.
```

**thread_roommate_conflict.txt#1** — distance: 0.5975; produced by: `chunker.py::split_documents`

```text
THREAD: Roommate situation isn't working. What now?

--- reply 2 (14 votes) ---
Room changes happen at the semester boundary almost always, and mid-semester only in fairly serious cases.
```

**thread_study_spots.txt#0** — distance: 0.5995; produced by: `chunker.py::split_documents`

```text
THREAD: Best study spots that aren't the library?

--- reply 1 (23 votes) ---
Ridgeway Café before 10am. Empty, quiet, good coffee, and they don't push you out.
```

### When do large employers close summer internship applications?

**thread_internship_timing.txt#0** — distance: 0.1514; produced by: `chunker.py::split_documents`

```text
THREAD: When should I start looking for a summer internship?

--- reply 1 (30 votes) ---
Earlier than feels reasonable. Large employers close applications in October and November for the following summer.
```

**thread_internship_timing.txt#1** — distance: 0.3159; produced by: `chunker.py::split_documents`

```text
THREAD: When should I start looking for a summer internship?

--- reply 2 (25 votes) ---
Smaller and local places hire in February and March, so if you missed autumn you have not missed everything.
```

**thread_internship_timing.txt#2** — distance: 0.3922; produced by: `chunker.py::split_documents`

```text
THREAD: When should I start looking for a summer internship?

--- reply 3 (19 votes) ---
The careers office reviews CVs on a drop-in basis and the queue is almost never longer than one person.
```

**thread_laundry_timing.txt#0** — distance: 0.7165; produced by: `chunker.py::split_documents`

```text
THREAD: When is laundry actually free in the dorms?

--- reply 1 (27 votes) ---
Tuesday and Wednesday mornings, every building. Sunday evening is the worst and it isn't close.
```

**thread_professor_email.txt#2** — distance: 0.7234; produced by: `chunker.py::split_documents`

```text
THREAD: Do professors actually answer email?

--- reply 3 (15 votes) ---
Empty office hours is the biggest unused resource here and I say that having wasted a year not going.
```

## Five sampled chunks, checked three times

Sample selection matches `app.py::cmd_chunks` with `-n 5`: stride across
the 75 chunks from `chunker.py::split_documents`.
The same sample positions are checked each pass, with no code or corpus changes.

### Chunk sample — run 1

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

### Chunk sample — run 2

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

### Chunk sample — run 3

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
