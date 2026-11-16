# MongoDB Progress

## Course
- **Course:** MongoDB's official course (MongoDB University / learn.mongodb.com)
- **Current section:** Introduction to MongoDB unit ✅ DONE. Next: the next unit in the course. Cluster0 is ACTIVE (M0 free, AWS, 1 region) with sample data loaded.
- **Start next session with:** they tried `{ title: 'godfather' }`. Real title is "The Godfather". Ask if it found anything and why not (exact match, case-sensitive). Movie doc fields seen: `genres`/`cast` are arrays, `awards`/`imdb` are embedded objects.

## Current position
- **Next step:** Watch the next lesson in the Introduction section, then tell Claude which one.

## Topics
⬜ not started · 🟨 in progress · ✅ mastered

| # | Topic | Status |
|---|---|---|
| 1 | What MongoDB is | 🟨 |
| 2 | Setup: Atlas / local, mongosh, Compass | 🟨 (Atlas M0 cluster created; mongosh & Compass not yet) |
| 3 | Databases, collections, documents, `_id` | 🟨 (hierarchy + browsing in Data Explorer; `_id`/BSON not yet) |
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
- Hierarchy order: first put cluster before collection/database, fixed it after a hint. Re-quiz: document → collection → database → cluster.
- Atlas account vs database user: didn't notice there were two logins. Explained with landlord login vs apartment key; then answered correctly that an app uses the database user. Re-quiz later.
- IP Access List: "idk" on 2026-11-15 when tired, answered correctly the next day after creating the cluster, but in the end-of-unit check forgot it again (said only username + password) until nudged. **Keep re-quizzing: connecting needs database user AND IP on access list.**
- Prefers a very simple explanation of each lesson first, then check questions.
- Knows JS well (types, objects, strings vs numbers). Don't over-explain JS basics; only explain what's MongoDB-specific.
- The Atlas intro video lists many advanced features (Search, Vector Search, Charts, Data Federation...). Told to ignore them for now.

## Session log
| Date | Course section | What we covered | Notes |
|---|---|---|---|
| 2026-11-15 | — | Set up this folder | Ready to start |
| 2026-11-15 | Intro, lesson 1: Atlas | What a database is, MongoDB documents vs SQL "spreadsheet", what Atlas is (cloud MongoDB, cluster, free cluster, replication, drivers) | Answered check questions correctly. Exercise: wrote 2 user documents in chat, the 2nd with an extra field (based on my example, not from scratch). Skipped writing `practice/01-intro.js`; will write files next time. |
| 2026-11-15 | Intro, lesson 2: foundations | Distributed database (nodes, redundancy, latency), document model (JSON-like, one doc = one entity, collections), flexible schema / polymorphic data (posts example) | Answered both check questions correctly (data survives node failure; products with shared `price` and t-shirt-only `size`). |
| 2026-11-15 | Intro, lesson 3: architecture | Hierarchy (document → collection → database → node → cluster), CAP theorem (bank analogy), replication / replica set / `mongod`, read & write concerns, sharding vs replication | Hierarchy order needed one hint. Replication vs sharding correct. Flagged a course error: write concern "majority" is slower but safer, not faster. |
| 2026-11-15 | Intro, lesson 4: Atlas infrastructure & security | Self-managed vs Atlas, cloud providers, regions (pick closest → less latency), availability zones / failover, database user vs IP Access List, RBAC | Region question correct. "idk" on the IP Access List question, tired, stopped there. Needs revisit. |
| 2026-11-16 | Intro, lesson 5: deploy first cluster | Created Atlas M0 cluster (Cluster0), auto security setup (own IP on access list), database user created, password saved outside the repo, org renamed. `.env` is created by hand, needed only once connecting from Node. Course outdated: mentions "Serverless" tier, now Flex. | IP Access List question now correct. Two-logins question: needed an explanation, then correct. |
| 2026-11-16 | Intro, lesson 6: exploring Atlas | Loaded sample data, navigated new Data Explorer (cluster → database → collection), Find bar idea (`{ field: value }`), M10+-only features (Real-Time Panel, Performance Advisor, Online Archive) | New Atlas UI differs a lot from the course; needed help finding sample data + Data Explorer. Course quizzes on M10 features: all correct. First query done alone: `{ year: 1986 }` in `sample_mflix.movies` (no `sample_analytics` in the cluster). Knew title needs quotes (string). |
| 2026-11-16 | Intro, conclusion + unit check | Unit recap; "relational" = SQL; we haven't actually connected yet | Hierarchy order ✅ (no hint this time), sharding ✅, connecting needs user + IP: needed a nudge on the IP part. |
