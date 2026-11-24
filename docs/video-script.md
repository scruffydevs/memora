# Memora: video script (about 5 minutes)

The spoken text below is about 740 words. At 150 words a minute that is about 4:55, at 145 about 5:05. Time one read-through, and if you run over, use the cuts listed at the end. Do not add anything. Speak slowly on the numbers and on the Gate slide.

---

## Slide 1: Title (0:00 to 0:15)

Hello, we are Team Larp from Ramaiah Institute of Technology, and this is Memora, our idea for the Know Thyself track.

Memora is an adaptive memory layer for people in the early stages of Alzheimer's, and for the people who care for them.

## Slide 2: The problem (0:15 to 0:50)

The WHO reports 57 million people living with dementia, and nearly 10 million new cases every year. In India, the LASI-DAD study estimates 8.8 million people over sixty. Alzheimer's is the most common cause of dementia, so Memora starts there.

In the early stages, the day fills with small, frightening questions. What was I doing? Who is this? Did I take my tablets? Where are my keys?

Caregivers cannot be there for every moment.

## Slide 3: Gaps (0:50 to 1:10)

Existing tools leave four gaps. Most are led by the caregiver, not the patient. Many rely on cameras or face databases. Few say who owns the data. And none link wearable signals to memory patterns.

## Slide 4: The solution (1:10 to 1:50)

Memora is a personal memory layer, built from one person's own life. It starts empty. Every note, person, medicine and wearable reading joins that person's record, and after a few weeks the system learns what is normal for them. Nothing is pooled with other patients.

It works in a loop. Capture: type or speak a note, and import wearable signals. Link: one clock, and one ID for each person, place and medicine. Recall and nudge: cited answers and calm nudges. Learn: feedback keeps it adapting as the person changes.

## Slide 5: Key features (1:50 to 2:40)

Seven key features.

A Today screen with calm, timely nudges. People profiles that say who someone is and what to mention. Capture by typing or voice.

Ask Memora recaps the day or finds something noted. It answers from the logged record and cites the entry, or says "I don't know."
Daily Signals turn sleep, steps and mood into weekly patterns. With the patient's consent, they become a clinician summary: how sleep, activity, mood and missed medicines have changed against that person's own baseline. A doctor sees change between visits, not only on appointment day. It supports the doctor's judgement. It never diagnoses.

And data exclusivity: a privacy gateway masks context before any model call.

## Slide 6: What runs today (2:40 to 3:05)

Now the technical side: what is built, and what is planned.

Today our prototype runs React and Tailwind, Node.js, PostgreSQL with pgvector, and the DeepSeek API, on synthetic data only.

Planned are AWS hosting in India, a small privacy gateway, an autoencoder in PyTorch, and ElevenLabs for spoken nudges, using generic phrases only.

## Slide 7: Eight stages (3:05 to 3:50)

Here is how data moves through Memora, in eight stages.

First, the inputs: wearable exports, notes, voice and medicine events. Ingest cleans each record and labels who can see it. Store keeps it all in PostgreSQL. Link puts everything on one clock and connects each event to the signals around it.

Then Learn. An autoencoder studies each person's own normal week, so it can tell when a week looks unusual. That feeds the clinician summary. It looks back, never ahead, and never diagnoses.

Next is the Gate, which we'll come to shortly. Serve gives back cited answers and nudges, Deliver shows them, and the person's feedback flows back into Learn.

Today, Ingest, Store, Link and Serve work in our prototype. The rest are planned.

## Slide 8: The Gate (3:50 to 4:25)

The Gate is our privacy core. A small model plus rules picks only the chunks a question needs, and masks names, places and dates.

Data has three tiers. Tier 0, like raw signals and location, is never sent to a model. Tier 1, like notes about visits and people, is masked, and sent only if needed.
Only masked text reaches the cloud model: DeepSeek in the prototype, on synthetic data, and a zero-retention provider in production. Real names are restored on return, and a receipt shows what left.

## Slide 9: Different by design (4:25 to 4:50)

What sets us apart is the combination: data exclusivity, a memory that adapts to one person, a clinician view built on their own baseline, and no face database.

Looking ahead, an optional wearable, such as Ray-Ban Meta smart glasses, could add hands-free capture and place-aware nudges. It would be opt-in, with the same Gate in front. That is a future direction, not part of today's prototype.

Our planned measures, not results yet: recall accuracy, correct "I don't know" answers, and a leak test with zero planted identifiers reaching the cloud.

## Slide 10: Close (4:50 to 5:00)

Memora is an adaptive memory layer that learns what is normal for one person, helps them and their doctor see change, and keeps their data theirs.

Your memory, your data. Thank you.

---

## Delivery notes

- If you run over 5:00, cut these in order: the smart-glasses paragraph's last sentence on slide 9, "Where are my keys?" on slide 2, the whole Tier 1 sentence on slide 8.
- Do not add claims about results, accuracy or clinical benefit. None exist yet.
- The clinician summary is planned, not built. Say "planned" if asked.
