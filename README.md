# vvit-clg-review-agent
Ananya — AI Voice Agent for Review Collection

An AI voice assistant that calls people and holds a real, structured conversation — asking questions, listening to answers, and logging clean, usable data at the end. This project uses it to collect student feedback for VVIT, but the same approach works for any business that needs to make or take a lot of repetitive phone calls.

Try the live demo → (https://Tulasikrishna3227.github.io/vvit-clg-review-agent/)

Why this matters for business owners

Most small and mid-sized businesses run into the same wall: someone has to be on the phone constantly — following up with leads, confirming appointments, checking in with customers, collecting feedback — and that work is repetitive, time-consuming, and expensive to staff.

An AI voice agent takes that repetitive load off a real person:


Cost — a human telecaller costs a salary, training time, and management overhead. A voice agent costs a few cents to a few rupees per minute, with no hiring, no attrition, no sick days.
Consistency — every caller gets asked the same questions, in the same tone, every time. No bad days, no skipped questions, no forgetting to log something.
Speed and scale — it can make (or take) hundreds of calls in the time a person makes a handful, and it never needs to go home at the end of the day.
Stress — the tedious, repetitive part of outbound/inbound calling — the part that burns people out — gets handled automatically, freeing up actual staff for the calls that need a human judgment call.


This isn't about replacing every human conversation. It's about removing the repetitive ones so people can focus on the ones that actually need a person.


Why this is a webpage instead of a phone number

The obvious way to "let people try it" would be handing out a real phone number to call. We deliberately didn't do that, for a few reasons:


Privacy — calling a real number means exposing a real telecom line, and callers dialing in expose their own number too. A browser-based call avoids that entirely — no phone numbers change hands on either side.
Ease of trying — most people won't dial an unfamiliar number just to test something. Clicking a button in a browser they're already looking at removes that friction completely.
Cost control — a public phone number is an open invitation for unlimited, uncontrolled calls. A web-based demo can be capped (call duration, monthly usage) so it can't run away in cost even if it gets shared widely.
No installs, no dialing, no waiting — the whole demo runs in the same tab, using the browser's own microphone. Click, talk, done.


This is the same reasoning a real business would apply: if you're rolling this out for customer feedback, appointment reminders, or lead qualification, a web widget on your existing site is almost always the safer, cheaper, easier entry point than publishing a phone line.


What the demo does

Click the circle, allow microphone access, and have an actual conversation with Ananya — she introduces herself, asks a handful of questions about your (or a student's) experience at VVIT, and wraps up the call. Everything said gets transcribed, summarized, and logged as structured data automatically.


How it's built

LayerToolVoice orchestrationVapiSpeech-to-textDeepgram — Flux General EnglishReasoning / conversation logicGPT-4.1Text-to-speechVapi (Elliot voice)Automation & data loggingn8n → Google SheetsDemo deliveryStatic webpage (GitHub Pages), Vapi Web SDK

Flow: person clicks to start → browser mic connects directly to the Vapi assistant → conversation happens in real time → once the call ends, Vapi analyzes the transcript and extracts structured fields (ratings, branch, feedback, etc.) → n8n picks up the finished call data and appends a clean row to a Google Sheet.


Try it yourself

Live demo → (replace with your GitHub Pages link)

No app, no download, no phone number required — just a microphone and a browser.


This is a demo instance with a capped call duration and monthly usage limit, to keep it available for everyone. If it's ever unresponsive, the cap was likely hit for the day/month.




Setup (if you want to run your own version)


Create an assistant on Vapi with your own system prompt, questions, and structured output schema.
Copy your Public API Key and Assistant ID from the Vapi dashboard.
Open index.html in this repo and paste them into the two placeholders near the bottom of the file (VAPI_PUBLIC_KEY, VAPI_ASSISTANT_ID).
Push to a GitHub repo, enable GitHub Pages in Settings → Pages, and your own version goes live at https://yourusername.github.io/your-repo/.
(Optional) Wire an n8n workflow to Vapi's call webhook to log structured results into Google Sheets, a CRM, or wherever you need them.
