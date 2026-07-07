# 🚕 Taxi

Artifact taxonomy built with AI in mind.

## The nature of AI

AI is a very capable software developer, perpetually on its first day.

No matter how many sessions it works on your project, it starts each from zero — rediscovering the architecture, re-inferring conventions, relearning the APIs, and reconstructing its idea of what your project does and how it's organized.

Of course, you have documentation.
And AI reads it.
So why does it still stumble?

## The sentence you can't read

Here is a sentence from a design document:

> Sessions are stored in Redis.

Is that how the system works today?
How it worked before the migration?
Something planned but not yet started?
Part of a rejected proposal?

From the words alone there's no way to tell.
And each possible interpretation implies something different to the reader, from *rely on this* to *do not build this*.

To be fair, the sentence might sit in a section called "Rejected designs," with the chosen design in another section.
But that's precisely the problem.
To judge whether the sentence is expected to be true, a reader has to check the surrounding context.
How much additional context is enough?
Well, that depends on how you wrote your document.

Because humans acquire knowledge, this problem is easily forgotten.
Once you know Memgraph was chosen over Redis, the ambiguity vanishes: the sentence is *obviously* describing a rejected design.

AI is smart.
Can't it do this?

## The clarity isn't in the document — it's in you

Acquired knowledge is why you can read your own design docs just fine.
The ambiguity is still on the page; you resolve it by supplying context the page doesn't contain.

If you've ever read an old document and casually breezed past the outdated bits, you understand the power of acquired knowledge.

AI doesn't acquire knowledge like humans do.
Context needs to be injected somewhere.
Every time AI reads that sentence about Redis, it has to re-determine how to interpret it.
If it doesn't see Redis in the code, should it add it? Ignore it? Update the documentation?

We're so used to writing and organizing information for readers who have acquired knowledge.
But we need to write and organize for readers who have none.

## Sort by frame

Taxi's answer: anchor every artifact to a **frame** — the kind of claim it makes — and sort information so that *where it lives* carries the frame.
When you start reading a document, you should know exactly how to interpret the information inside.

There are three frames, and the set is closed:

- **Explanatory** — past reasoning: why a choice was made
- **Descriptive** — present truth: what is true now.
- **Normative** — not-yet truth: what should be true.

It's really about **what it means when there's a gap between your artifact and your project**.
Take the Redis sentence again.

- In `explanatory/`, it makes no claim whether Redis is used or not. It means that using Redis was considered a factor or possible outcome in a decision. You don't read `explanatory/` to get a birds-eye view of the project. You read it to mine past reasoning in order to make a better design decision.
- In `descriptive/`, it claims that we currently use Redis. If we're actually not using Redis, the doc has a bug and should be updated. Artifacts in `descriptive/` must be describing the current system or they will steer AI in the wrong direction.
- In `normative/`, it claims that we should be using Redis. It doesn't claim that we're using Redis now. If we're not, that gap indicates that there's work to do.

Same words, three meanings.
The frame, not surrounding context, conveys the utility of a statement.
And it naturally conserves context, because agents can be instructed to only read the kind of information they need.

## Taxi

Taxi is a taxonomy for project knowledge: a directory layout that carries the frames, a contract (`AGENTS.md`) in every directory telling any reader — human or AI — how to treat what lives there.

That's it.
No runtime, no process, no new tooling.

```
docs/
  consumer/        for people USING the project
  contributor/     for people BUILDING it
    inbox/           raw input, not yet sorted
    explanatory/     why choices were made
    descriptive/     what's true now
    normative/       what should be true
```

### What to read next

- *Why do users get their own tree, outside the frames?* → [`docs/consumer/`](docs/consumer/AGENTS.md)
- *What exactly are the frames and their rules?* → [the reference](docs/consumer/reference.md), or [the full model](docs/contributor/descriptive/abstractions/taxonomy.md)
- *What about knowledge that lives in Jira or a wiki?* → [artifacts and pointers](docs/consumer/reference.md#entry-types-artifacts-and-pointers)
- *How is an AI told to read each folder?* → [making Taxi legible to your agent](docs/consumer/reference.md#making-taxi-legible-to-your-agent)
- *How do I adopt this in my repo?* → [using Taxi in practice](docs/consumer/patterns.md)
