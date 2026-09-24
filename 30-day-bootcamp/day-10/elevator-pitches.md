# Elevator Pitches (3 Versions)

> Every FDE needs to explain their solution clearly and quickly to different audiences. Prepare all three versions below and practice until they feel natural, not rehearsed.

---

## 30-Second Executive Version

**Audience:** C-suite, VP-level, board members -- people who care about business outcomes, not architecture diagrams.

**Pitch Text:**

> *[e.g., "Your team spends 75 hours a week answering 'where is my shipment?' calls, and your largest customer is threatening to leave because of it. We're building a real-time tracking solution that puts shipment status at your CS team's fingertips -- no more calling the warehouse, no more stale spreadsheets. Based on similar implementations, we expect a 60% reduction in tracking-related calls within 30 days of deployment. We can have a working proof of concept in front of your team in three weeks."]*

**Key Points to Emphasize:**

- *[e.g., "Lead with the cost of the problem (75 hours/week, $18M account at risk)"]*
- *[e.g., "Quantify the expected outcome (60% reduction)"]*
- *[e.g., "Give a clear timeline (3 weeks to POC)"]*
- *[e.g., "Do NOT mention specific technologies"]*

**What to avoid:** *Technical jargon, architecture details, feature lists. Executives buy outcomes, not components.*

---

## 60-Second Technical Version

**Audience:** Engineering managers, technical leads, architects -- people who need to believe the solution is feasible and well-designed.

**Pitch Text:**

> *[e.g., "The core problem is data fragmentation -- shipment status lives in three disconnected systems: the warehouse management system, carrier GPS feeds, and the legacy tracking database. None of them talk to each other in real time.*
>
> *Our solution is an event-driven integration layer that ingests data from all three sources into a unified data model. We're using [technology] for the streaming pipeline and [technology] for the API layer. The frontend is a lightweight React dashboard that connects to the existing Zendesk instance via their API, so CS reps don't need to switch tools.*
>
> *The architecture is intentionally simple for the POC -- we're optimizing for speed to value, not scale. But we're designing the data model and API contracts so the system can evolve into a production-grade platform without a rewrite.*
>
> *We'll have a working demo with live data in two weeks."]*

**Key Points to Emphasize:**

- *[e.g., "Name the root technical problem (data fragmentation)"]*
- *[e.g., "Explain the architecture at a level that builds confidence"]*
- *[e.g., "Acknowledge the POC/production tradeoff explicitly"]*
- *[e.g., "Show you've thought about integration with their existing tools"]*

**What to avoid:** *Oversimplifying (they will see through it), over-engineering (they will question your judgment), ignoring existing systems (they will worry about disruption).*

---

## 2-Minute Detailed Version

**Audience:** Mixed audience -- stakeholder meetings with both business and technical attendees, or a prospect meeting where you need to be thorough.

**Pitch Text:**

> *[Write your 2-minute pitch here. Structure it as follows:]*
>
> **The Problem (30 seconds):**
> *[Describe the business pain with specific numbers. Make the audience feel the problem.]*
>
> *[e.g., "Every day, your customer service team receives over 200 calls asking the same question: 'Where is my shipment?' Each call takes an average of 15 minutes because your reps have to check three different systems, sometimes calling the warehouse directly. That's 75 hours of labor per week spent on a question that should be answered instantly. Meanwhile, your NPS has dropped from 58 to 32, and your largest account -- worth $18 million a year -- has formally told you they're evaluating alternatives."]*
>
> **The Solution (30 seconds):**
> *[Describe what you're building in plain language. Focus on what changes for the user.]*
>
> *[e.g., "We're building a unified tracking system that gives your CS team -- and eventually your customers directly -- real-time visibility into every shipment. When a rep gets a call, they'll type a tracking number and instantly see the shipment's current location, status history, and predicted arrival time. No more calling the warehouse. No more stale data."]*
>
> **How It Works (30 seconds):**
> *[Explain the approach at a level appropriate for a mixed audience.]*
>
> *[e.g., "Under the hood, we're connecting your three data sources -- the warehouse system, carrier GPS feeds, and your tracking database -- into a single real-time pipeline. We're also adding proactive notifications, so when a shipment is delayed, the customer gets an email before they have to call."]*
>
> **Why Now and Why Us (30 seconds):**
> *[Create urgency and differentiate your approach.]*
>
> *[e.g., "The reason to act now is that your largest customer's contract is up for renewal in Q4. A working solution by then changes the conversation from 'we're sorry' to 'look what we've built for you.' As for why us -- we've done this before. We know the failure modes, we can move fast, and we'll have a proof of concept with your live data in three weeks. If it doesn't demonstrate clear value, you'll know quickly and at low cost."]*

**Key Points to Emphasize:**

- *[e.g., "Open with a number that creates urgency"]*
- *[e.g., "Describe the user experience, not the system architecture"]*
- *[e.g., "Connect the timeline to a real business event (Q4 renewal)"]*
- *[e.g., "End with a low-risk proposition (POC = low cost to learn)"]*

**What to avoid:** *Rushing through it, reading from notes, spending too long on any one section, getting pulled into Q&A before finishing (say "great question -- let me finish the overview and then I'll come back to that").*

---

## Practice Checklist

- [ ] I can deliver the 30-second version without notes
- [ ] I can deliver the 60-second version without notes
- [ ] I can deliver the 2-minute version without notes
- [ ] I have practiced with a colleague and received feedback
- [ ] I can pivot between versions depending on who walks into the room
- [ ] I can handle the question "so what exactly do you do?" with any of these

---

*Record yourself delivering each pitch. Watch it back. You will notice things you cannot hear in the moment.*
