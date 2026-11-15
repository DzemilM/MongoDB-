# MongoDB Progress

## Course
- **Course:** MongoDB's official course (MongoDB University / learn.mongodb.com)
- **Current section:** Introduction, lesson 4 (Atlas infrastructure & security) watched, check not finished. Next video: deploying your first cluster

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
- Hierarchy order: first put cluster before collection/database, fixed it after a hint. Re-quiz: document → collection → database → cluster.
- **Start next session here:** Atlas security. Said "idk" to "friend has user+password but can't connect, what's missing?" (answer: IP Access List). Was tired. Also asked "is Atlas local only?" Clarified it's in the cloud, reachable from anywhere you allow. Re-explain database user vs IP Access List gently before creating the cluster.
- Prefers a very simple explanation of each lesson first, then check questions.
- The Atlas intro video lists many advanced features (Search, Vector Search, Charts, Data Federation...). Told to ignore them for now.

## Session log
| Date | Course section | What we covered | Notes |
|---|---|---|---|
| 2026-11-15 | — | Set up this folder | Ready to start |
| 2026-11-15 | Intro, lesson 1: Atlas | What a database is, MongoDB documents vs SQL "spreadsheet", what Atlas is (cloud MongoDB, cluster, free cluster, replication, drivers) | Answered check questions correctly. Exercise: wrote 2 user documents in chat, the 2nd with an extra field (based on my example, not from scratch). Skipped writing `practice/01-intro.js`; will write files next time. |
| 2026-11-15 | Intro, lesson 2: foundations | Distributed database (nodes, redundancy, latency), document model (JSON-like, one doc = one entity, collections), flexible schema / polymorphic data (posts example) | Answered both check questions correctly (data survives node failure; products with shared `price` and t-shirt-only `size`). |
| 2026-11-16 | Intro, lesson 3: architecture | Hierarchy (document → collection → database → node → cluster), CAP theorem (bank analogy), replication / replica set / `mongod`, read & write concerns, sharding vs replication | Hierarchy order needed one hint. Replication vs sharding correct. Flagged a course error: write concern "majority" is slower but safer, not faster. |
| 2026-11-16 | Intro, lesson 4: Atlas infrastructure & security | Self-managed vs Atlas, cloud providers, regions (pick closest → less latency), availability zones / failover, database user vs IP Access List, RBAC | Region question correct. "idk" on the IP Access List question, tired, stopped there. Needs revisit. |
