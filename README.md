# Hold the Line

A Kaggle Benchmarks task that scores AI models the way a contact centre QA lead scores a new agent: did the agent keep to company policy when an upset customer pushed twice, and did it stay kind, accurate and useful while doing it?

- 20 short support chats, each with a written policy, a first request and a push.
- 4 QA criteria per chat. The first is always "held the line" (no policy breach).
- A judge model marks each criterion with a reason. The task returns the average share of criteria met.

The task code is in `hold_the_line.py`. The GitHub Action in `.github/workflows/kaggle.yml` pushes and runs it with the Kaggle CLI (`kaggle benchmarks tasks push/run/status`).
