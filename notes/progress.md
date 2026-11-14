# MongoDB Progress

## Course
- **Course:** MongoDB's official course (MongoDB University / learn.mongodb.com)
- **Current section:** Introduction, lesson 2 (distributed database, document model, flexible schema) done. Next video: MongoDB architecture

## Current position
- **Next step:** Watch the next lesson in the Introduction section, then tell Claude which one.

## Topics
⬜ not started · 🟨 in progress · ✅ mastered

| # | Topic | Status |
|---|---|---|
| 1 | What MongoDB is | 🟨 |
| 2 | Setup: Atlas / local, mongosh, Compass | 🟨 (knows what Atlas is, nothing set up yet) |
| 3 | Databases, collections, documents, `_id` | ⬜ |
| 4 | CRUD | ⬜ |
| 5 | Query operators | ⬜ |
| 6 | Projection, sort, limit, pagination | ⬜ |
| 7 | Update operators, upsert | ⬜ |
| 8 | Data modeling: embed vs reference | ⬜ |
| 9 | Indexes | ⬜ |
| 10 | Aggregation pipeline | ⬜ |
| 11 | Schema validation | ⬜ |
| 12 | Node.js driver | ⬜ |
| 13 | Mongoose | ⬜ |
| 14 | MongoDB + Express REST API | ⬜ |
| 15 | Transactions, common mistakes | ⬜ |

## Weak spots to revisit
- No prior database knowledge at all (not even SQL). Explain any SQL comparison from scratch.
- The Atlas intro video lists many advanced features (Search, Vector Search, Charts, Data Federation...). Told to ignore them for now.

## Session log
| Date | Course section | What we covered | Notes |
|---|---|---|---|
| 2026-11-15 | — | Set up this folder | Ready to start |
| 2026-11-15 | Intro, lesson 1: Atlas | What a database is, MongoDB documents vs SQL "spreadsheet", what Atlas is (cloud MongoDB, cluster, free cluster, replication, drivers) | Answered check questions correctly. Exercise: wrote 2 user documents in chat, the 2nd with an extra field (based on my example, not from scratch). Skipped writing `practice/01-intro.js`; will write files next time. |
| 2026-11-15 | Intro, lesson 2: foundations | Distributed database (nodes, redundancy, latency), document model (JSON-like, one doc = one entity, collections), flexible schema / polymorphic data (posts example) | Answered both check questions correctly (data survives node failure; products with shared `price` and t-shirt-only `size`). |
