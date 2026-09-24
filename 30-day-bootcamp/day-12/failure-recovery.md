# Demo Failure Recovery Strategies

> Every FDE will experience a demo failure. The difference between a junior and a senior FDE is not whether things break -- it is how they recover. This document prepares you for the three most common failure scenarios.

---

## Scenario 1: API/Service Goes Down During Demo

### What Happens

You click a button or navigate to a page, and instead of data, you see a loading spinner that never resolves, a 500 error, a connection refused message, or a blank screen.

### Signs It Is Happening

- Page loads but shows "No data" or a spinner that persists longer than 5 seconds
- Browser console shows network errors (if you happen to glance at it -- do NOT open dev tools during a demo)
- A feature that worked in rehearsal now returns an error

### How to Recover

**Immediate (0-5 seconds):**
1. Do not stare at the error. Do not narrate the failure ("oh, it's not loading...").
2. Take a breath. This is your moment to show composure.

**Short-term (5-30 seconds):**
3. Try ONE quick recovery action:
   - Refresh the page
   - Navigate to a different section that may still work
   - Switch to a different demo data example

**If recovery fails (30+ seconds):**
4. Switch to your backup:
   - Pre-captured screenshots: *"Let me show you the expected result while the live environment recovers."*
   - Pre-recorded video: *"I have a walkthrough recorded -- let me play that."*
   - Whiteboard/verbal: *"Let me walk you through what you would see here..."*

### What to Say to the Audience

**Do say:**
> - "Let me pull up the recorded version while this recovers."
> - "This is live data from your systems, and it looks like the connection is having a moment. Here is what you would normally see..." *(show screenshot)*
> - "One of the benefits of a POC is finding exactly these kinds of edge cases. Let me note this and move on to the next part."

**Do NOT say:**
> - "I don't know what's happening."
> - "It was working five minutes ago, I swear."
> - "Let me try to debug this..." *(opens terminal in front of client)*
> - "Sorry, sorry, sorry..."

### Post-Demo Actions

- [ ] Diagnose the root cause within 1 hour of the demo
- [ ] Send a follow-up email: *"The live environment had a brief connectivity issue during our session. Here is a recording of the full demo working as expected: [link]"*
- [ ] Fix the issue and offer a brief live follow-up if the client wants one

---

## Scenario 2: Model Returns Wrong Answer

### What Happens

You ask the AI/ML component a question during the demo, and it returns an incorrect, irrelevant, or embarrassing answer. Examples: wrong classification, hallucinated data, nonsensical response, or an answer that contradicts what you just told the audience.

### Signs It Is Happening

- The output does not match what you expected based on rehearsal
- An audience member's expression changes (confusion, skepticism)
- The response contains information you know is incorrect

### How to Recover

**Immediate (0-3 seconds):**
1. Acknowledge it without panic. Do NOT pretend the answer was correct.
2. Do NOT try to explain away a clearly wrong answer.

**Short-term (3-15 seconds):**
3. Use one of these recovery strategies:

   **Strategy A -- Reframe as a teaching moment:**
   > "This is actually a great example of why human oversight is part of our design. The model is not always right -- what matters is that the system flags low-confidence results for human review."

   **Strategy B -- Try an alternative input:**
   > "Let me try a slightly different input -- the phrasing can affect results, which is something we're tuning." *(Use a pre-tested input you know works)*

   **Strategy C -- Show the expected result:**
   > "That's not the typical response. Let me show you what the output looks like with a well-formed input." *(Switch to a pre-captured screenshot of a correct result)*

**If it keeps failing:**
4. Move on gracefully:
   > "The model is still being fine-tuned for your specific data. The architecture is sound -- it's the training data that needs refinement. Let me show you the next feature while this calibrates."

### What to Say to the Audience

**Do say:**
> - "Great catch -- this is exactly the kind of output we're tuning the model to handle better."
> - "This tells us the model needs more examples of [this type of input]. That's a solvable problem."
> - "No model is 100% accurate, which is why our design includes a confidence score and human review step."

**Do NOT say:**
> - "That's weird, it worked before."
> - "I have no idea why it said that."
> - *(Silently trying the same thing again and again)*
> - "AI is unpredictable, you know..." *(This destroys trust)*

### Post-Demo Actions

- [ ] Investigate why the model gave the wrong answer
- [ ] Add the failing input to your test suite
- [ ] Send a follow-up with the corrected result: *"I looked into the response we saw during the demo. Here is what happened and how we're addressing it: [explanation]"*
- [ ] Consider adding a "known good inputs" list for future demos

---

## Scenario 3: Data Loading Fails

### What Happens

The demo depends on data that should have been loaded or refreshed, but the dataset is missing, empty, stale, or corrupted. The dashboard shows zero results, the search returns nothing, or the numbers are clearly wrong.

### Signs It Is Happening

- Dashboard shows "0 shipments" when you expect thousands
- Charts are empty or show flat lines
- Search returns no results for tracking numbers you know exist
- Numbers are wildly different from what you rehearsed with

### How to Recover

**Immediate (0-5 seconds):**
1. Do not draw attention to the empty state if the audience hasn't noticed yet.
2. Navigate away from the empty view.

**Short-term (5-30 seconds):**
3. Try these recovery steps:
   - Check if there's a filter applied that's hiding data (common mistake)
   - Switch to a different data view or time range
   - Use a direct URL to a specific record you know exists

**If data is truly missing:**
4. Switch to backup:

   **Strategy A -- Use pre-loaded screenshots:**
   > "The data refresh is still running -- here is what the dashboard looks like with a full dataset." *(Show screenshot)*

   **Strategy B -- Use a secondary environment:**
   > "Let me switch to our staging environment, which has a complete dataset." *(If you have one)*

   **Strategy C -- Narrate over the architecture:**
   > "While the data catches up, let me walk you through the architecture and what each section displays when populated."

### What to Say to the Audience

**Do say:**
> - "The data pipeline is still syncing -- this is a POC, so we're running the refresh on a schedule rather than continuously. Here is what the full view looks like." *(show backup)*
> - "Let me pull up a pre-populated view so you can see the full experience."
> - "This is one of the things we'd automate in production -- the data refresh runs continuously rather than on a schedule."

**Do NOT say:**
> - "Where did all the data go?"
> - "I forgot to load the data." *(Even if true, rephrase as "the refresh hasn't completed yet")*
> - "This never happened in testing."
> - *(Typing commands into a terminal to reload data while everyone watches)*

### Post-Demo Actions

- [ ] Set up an automated data refresh that runs 30 minutes before every demo
- [ ] Create a pre-demo checklist that includes verifying data is loaded
- [ ] Consider having a "demo dataset" that is always available, separate from live data
- [ ] Send follow-up with screenshots or recording of the fully populated demo

---

## Universal Recovery Principles

1. **Composure is more important than the fix.** Clients are evaluating YOU as much as the product. Staying calm under pressure builds trust.

2. **Never debug in front of the client.** If you cannot fix it in one click, move on.

3. **Always have three backups:**
   - Screenshots of every key screen
   - A pre-recorded video walkthrough
   - The ability to narrate the experience verbally

4. **Acknowledge, don't apologize.** "Let me show you the expected result" is better than "I'm so sorry."

5. **Follow up within 24 hours.** A quick email with a working demo or recording turns a failure into a demonstration of reliability.

---

## Pre-Demo Failure Prevention Checklist

- [ ] Test the full demo flow within 1 hour of the actual demo
- [ ] Verify all data is loaded and current
- [ ] Check that all APIs and services are responding
- [ ] Confirm your internet connection is stable (use wired if possible)
- [ ] Close all unnecessary applications and browser tabs
- [ ] Disable system notifications (Slack, email, calendar)
- [ ] Have screenshots saved locally (not in cloud storage that requires auth)
- [ ] Have the recorded video walkthrough downloaded locally
- [ ] Know the phone number of someone who can restart services if needed
- [ ] Have a plan for "what do I show if I have zero technology available?"

---

*The best demo recovery is the one the audience never notices. Prepare so thoroughly that failure is a brief detour, not a dead end.*
