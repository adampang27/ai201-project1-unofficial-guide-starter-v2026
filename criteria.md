# Acceptance criteria — The Unofficial Guide

Five criteria that say what "working" means for this system, written in unit 1
**before** any results existed.

An acceptance criterion names a target: a number, a count, a rate, or something
a person could plainly observe. *"Retrieval works"* is an opinion. *"For at
least 4 of my 5 test questions, the top results include a chunk containing the
answer"* is a criterion.

Under each one, write a sentence or two on **why that target** and not a
stricter or looser one. A reason that says something about your corpus or your
pipeline earns credit; *"80% seemed reasonable"* does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---

## 1. Retrieved chunks contain the answer

For at least 4 of my 5 test questions, the retrieved chunks include one that
contains the answer.

**Why this target:**
To test retrieval accuracy. My questions include specific facts and places that come from the corpus documents. A 5 out of 5 target is unrealistic because advice_threads is informal forum replies where students use casual phrasing and slang (like the late library hours being a "trap", or "stacking" courses), so the query wording might not always match. But looser than 4 of 5 would mean missing 40% of test questions on a small 23 document corpus, which would be considered too loose to count as working.

---

## 2. Every answer names a source

Every answer the system produces names at least one source document.

**Why this target:**
To function as a good RAG system, it needs to show proof of where it gets its information from so the user can fact-check the answers. This has to be all five (not 4 of 5) because source citation is built right into the prompt and pipeline. For an answer to have no source, something would have to completely break. Either the prompt failed to ask for citations, some data was lost during retrieval, or the model hallucinated without using the chunks at all.

---

## 3. The relevance gate stops out-of-corpus questions

When I ask a question my documents clearly don't cover, the relevance gate
stops it and the system returns "I don't have enough information about that" —
in at least 4 of 5 tries.
 
<!-- The five questions are the ones in `OUT_OF_SCOPE` at the bottom of
     `questions.py`, and `run_eval.py` puts them through the gate and writes
     what happened into your run log. Swap them for your own if you'd rather —
     just keep five of them, or the "4 of 5" above has nothing to be 4 of. -->

**Why this target:**
One miss out of five would be okay as there are some questions related to the source document.
Two misses out of five is too loose of a target as it would mean the gate is wrong about questions that share nothing in common with the corpus. Mongolia, a diesel engine, the 1994 World Cup, a drug dose share almost nothing with advice_threads but the Rust question can almost be attributed to to the thread on laptop specifications.

<!-- What did your distances look like when you set the cutoff in Milestone 4?
     Was there a clean gap, or did the two groups overlap? -->

---

## 4. Chunks are complete replies

At least 4 of 5 sampled chunks are one reply, with no sentence cut off at either end.

<!-- YOU WRITE THIS ONE.

     How would you know if your chunks were the right size? Name something
     countable or observable.

     Examples of the right shape — don't copy these, they should come from
     what you actually saw in Milestone 3:
       - "At least 4 of 5 sampled chunks read as a complete thought, with no
          sentence cut in half at either end."
       - "No chunk is shorter than 200 characters, since anything below that
          in my corpus turned out to be a heading with no content under it." -->

**Why this target:**
In advice_threads, documents are made of separate replies. A chunk would be too small if it were describing something / giving attributes about something but cut off before you could tell what it was describing. On the contrary, a chunk would be too big if it started changing topics / describing a different thing by combining replies into the same chunk. 4 of 5 keeps chunks centered on one reply and idea, with a little room for an extra long reply.

---

## 5. When a thread names more than one place or time, answers include more than one

When a thread names more than one place or time, at least 4 of 5 answers include
more than one of them.

<!-- YOU WRITE THIS ONE TOO.

     Pick something you actually care about getting right. It could be about
     speed, about refusals, about a particular kind of question your corpus
     handles badly, about source attribution being correct rather than merely
     present — anything, as long as it names a number or an observable
     outcome. -->

**Why this target:**
In the advice_threads corpus, there are threads with questions that can have multiple answers. A complete and well-designed system would output all information necessary when asked. For example, asking about good study spots should return multiple possible locations, and internship timing names both fall and spring windows. Getting at least two options into 4 of 5 answers shows the system actually pulls multiple possibilities instead of stopping at the first one it finds.


---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 2 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath it, like this:

         ## 1. Retrieved chunks contain the answer

         For at least 4 of my 5 test questions, the retrieved chunks include
         one that contains the answer.

         **Why this target:** ...

         > **Revised in unit 2:** For at least 4 of 5 questions, the top three
         > results contain the answer.
         >
         > **Why revised:** I couldn't judge "the chunks include one that
         > contains the answer" the same way twice — I scored two questions
         > differently on Monday than on Wednesday. The new version is
         > something I can actually check.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "I said 4 of 5 but got 2 of 5, so 2 of 5 is more realistic."

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.

     The whole reason the originals stay visible is so someone can see what you
     said before you knew the answer.
     ───────────────────────────────────────────────────────────────────────── -->
