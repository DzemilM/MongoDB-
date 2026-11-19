# MongoDB Progress

## Course
- **Course:** MongoDB's official course (MongoDB University / learn.mongodb.com)
- **Current section:** Unit 2 (MongoDB document model), lessons 1 (document structure, JSON vs BSON), 2 (BSON data types, `_id`/ObjectId) 3 (Atlas UI: create DB/collections, insert doc, query) 4 (data modeling intro) and 5 (embedding vs referencing) done. Next: next lesson in unit 2. Cluster0 is ACTIVE (M0 free, AWS, 1 region) with sample data loaded.
- **Open, low priority:** `{ title: 'godfather' }` returned some other movie; said "idk" why, dropped it. Retry next time they're in Atlas (exact match, case-sensitive). Movie doc fields seen: `genres`/`cast` are arrays, `awards`/`imdb` are embedded objects.

## Current position
- **Start next session with (requested):** a quick recap of unit 2 so far (document structure, golden rule, JSON vs BSON, BSON types + Decimal128, `_id`/ObjectId, array match = contains, relationship types, embed vs reference) + a few questions, focusing on weak spots. Then continue with the next lesson.

## Topics
⬜ not started · 🟨 in progress · ✅ mastered

| # | Topic | Status |
|---|---|---|
| 1 | What MongoDB is | 🟨 |
| 2 | Setup: Atlas / local, mongosh, Compass | 🟨 (Atlas M0 cluster created; mongosh & Compass not yet) |
| 3 | Databases, collections, documents, `_id` | 🟨 (hierarchy, browsing, JSON vs BSON, BSON types, `_id`/ObjectId) |
| 4 | CRUD | 🟨 (inserted first doc in Atlas UI; find with simple filters) |
| 5 | Query operators | 🟨 (equality on array field = "contains") |
| 6 | Projection, sort, limit, pagination | ⬜ |
| 7 | Update operators, upsert | ⬜ |
| 8 | Data modeling: embed vs reference | 🟨 (entities/attributes, relationship types, embed vs reference basics; needs a real modeling exercise) |
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
- BSON types: said "idk" on why `released` shows as `ISODate(...)`; unclear on why a DB needs a Date type. Explained (JSON has no dates, strings can't be compared/sorted as dates). Re-quiz.
- Embed vs reference: for unbounded growth (50k comments) said "embed, but reference as it grows". Decide up front based on possible growth, since switching later means rewriting data + code. Re-quiz.
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
| 2026-11-19 | Unit 2, lesson 1: document model | Field-value pairs, unique descriptive field names, golden rule (accessed together → stored together), arrays + embedded docs, JSON vs BSON, flexible schema (add fields anytime), limits 16 MB / 100 nesting levels | Golden rule (blog tags → array inside post) ✅. "idk" on ISODate; after explanation picked `released` for date query, reason was meaning not type. Also "idk" on godfather result, dropped. |
| 2026-11-19 | Unit 2, lesson 2: BSON data types | Int32/Int64/Double/Decimal128 (money → Decimal128), Date = ms since 1970, `_id` required + unique, auto ObjectId (timestamp inside). Flagged: ObjectId is its own type, not a string → string `_id` search won't match. | All 3 check questions ✅ without help (Decimal128 for price, auto `_id`, email array with good reasoning). |
| 2026-11-19 | Unit 2, lesson 3: Atlas UI hands-on | Created DB `'mflix_merchandise'` with `swag` + `memorabilia` (new Data Explorer UI differs from course), inserted autographed-photo doc with chosen types, queried `{ cast: "John Wayne" }` (21 results), array field match = contains (like `.includes()`) | Insert done alone and picked **Decimal128 for `value` unprompted** ✅; noticed auto ObjectId `_id` ✅. Array-match "why": guessed `==`, then `.find()`, got there with hints → re-quiz. |
| 2026-11-19 | Unit 2, lesson 4: data modeling intro | Entity = document/collection, attribute = field; one-to-one, one-to-many, many-to-many; "ask from both sides" trick. Flagged course error: studio ↔ movie is one-to-many, not one-to-one. | All 3 relationship questions ✅ without help (user→posts, posts↔tags, user↔profile picture). |
| 2026-11-19 | Unit 2, lesson 5: embedding vs referencing | Embed = inside doc (one lookup), reference = store `_id`s of docs in another collection (two lookups, one source of truth). 3 decision questions: shown together? used/updated on its own? grows without limit? Course note: bidirectional refs usually avoided. Mentioned subset pattern (embed newest comments). | Tags → embed ✅, author → reference ✅ (reason: changes often; added: update once instead of every post). Comments: "embed, then reference as it grows". Corrected: decide up front → reference. |
