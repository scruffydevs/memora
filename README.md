# Memora

**An adaptive memory layer for people in the early stages of Alzheimer's, and the people who care for them.**

Team Larp, Ramaiah Institute of Technology. wHACKiest 2026, Round 1 (idea and pitch), Track 3: Know Thyself.

> Status: this is an **idea submission**. There is no Memora app yet. Each part below is marked **Prototype** (something we have run) or **Planned** (design only).

## The problem

The WHO reports 57 million people living with dementia worldwide and nearly 10 million new cases a year. The LASI-DAD study estimates 8.8 million Indians aged 60+ live with dementia. (These figures cover dementia as a whole, not Alzheimer's alone. Alzheimer's is the most common cause.)

In the early stages the day fills with small, frightening questions: *What was I doing? Who is this? Did I take my tablets? Where are my keys?* Caregivers cannot be there for every moment.

## The idea

Memora is a **personal memory layer built from one person's own life**. It starts empty. Every note, person, medicine and wearable reading joins that person's record, and after a few weeks of use it learns what is normal for them. Nothing is pooled with other patients.

Loop: **Capture** (type or speak, import wearable signals) -> **Link** (one clock, one ID per person, place and medicine) -> **Recall and nudge** (cited answers, calm explained nudges) -> **Learn** (feedback keeps it adapting).

### Key features

1. Today screen with calm, timely nudges
2. People profiles (who someone is, what to mention)
3. Capture by typing or voice
4. Ask Memora: answers cite the log, or say "I don't know"
5. Evening recap (optional)
6. Daily Signals: sleep, steps and mood as weekly patterns. With the patient's consent, a **clinician summary** of how things changed against that person's own baseline. It describes change and never diagnoses.
7. Data exclusivity: a privacy gateway masks context before any model call

## Architecture (eight stages)

| # | Stage | What it does | Tech | Status |
|---|-------|--------------|------|--------|
| 1 | Inputs | Wearable exports, notes, voice, medicine events | Browser speech-to-text | Planned |
| 2 | Ingest | Clean, dedupe, one time zone, visibility label | Node.js | Prototype |
| 3 | Store | Encrypted vault, time-indexed signals, searchable entries | PostgreSQL + pgvector | Prototype |
| 4 | Link | Time alignment, entity linking, event-signal links | SQL joins, entity tables | Prototype |
| 5 | Learn | Personal baseline, recall ranking, nudge timing | Autoencoder (PyTorch) | Planned |
| 6 | Gate | Picks need-to-know chunks, masks the rest | Small model + rules | Planned |
| 7 | Serve | Cited recall, weekly insights, nudges | DeepSeek API, masked text only | Prototype |
| 8 | Deliver | Large-type card, spoken nudge, receipt of what left | React; ElevenLabs TTS | Planned |

Planned hosting: AWS, India region (RDS PostgreSQL, App Runner, S3 + CloudFront).

### The Gate (privacy core)

A small model plus rules selects only the chunks a question needs and masks names, places and dates. Only masked text reaches the cloud model. Real names are restored on return, and a receipt shows what left.

- **Tier 0**: never sent to a model (raw signals, location, medicine detail, anything marked private)
- **Tier 1**: masked, and sent only if the question needs it (notes about visits and people)
- **Tier 2**: low sensitivity, sent as written

Prototype: DeepSeek API on **synthetic data only**. Production: a zero-retention provider.

## What exists today

- Prototype stack: React + Tailwind, Node.js, PostgreSQL + pgvector, DeepSeek API (synthetic data only).
- An earlier prototype ran retrieval and ranking over 10,678 indexed items in about 0.1 s. The AI step comes next.
- No results are claimed for recall accuracy, insight quality or clinical value.

## Planned evaluation (not results)

Recall accuracy on questions from the log; correct "I don't know" on unanswerable questions; insight recovery on planted patterns; nudge acceptance; a leak test with a target of zero planted identifiers reaching the cloud. Test patients are synthetic, so we would measure the system, not clinical value. Open data: PMData (Fitbit) plus a synthetic cohort.

## Future direction

An optional wearable, such as Ray-Ban Meta smart glasses, for hands-free capture and place-aware nudges. Opt-in, behind the same Gate. Not part of the prototype; platform access is unverified.

## Repository contents

- `docs/Track3_Submission_Deck.pptx`: official-template Round 1 deck
- `docs/Memora_Video_Deck.pptx`: deck used in the pitch video
- `docs/video-script.md`: the roughly 5-minute video script

## Sources and caveats

WHO dementia fact sheet (2021 data); LASI-DAD (India, age 60+). Comparison with OurLife, I Remember, RecallCue and Vela Vision is based on their public pages and listings, not independent evaluation. Memora is a support tool and does not diagnose.
