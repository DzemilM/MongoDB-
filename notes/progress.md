# MongoDB Progress

## Course
- **Course:** MongoDB's official course (MongoDB University / learn.mongodb.com)
- **Current section:** Unit 3 (connecting), lessons 1 (connection string), 2 (install + connect with mongosh) 3 (troubleshooting connections) and 4 (using mongosh: insertOne/find, JS, load()) done. Next: next lesson in the course. Cluster0 is ACTIVE (M0 free, AWS, 1 region) with sample data loaded. mongosh 2.14.1 installed via winget.
- **Open, low priority:** `{ title: 'godfather' }` returned some other movie; said "idk" why, dropped it. Retry next time they're in Atlas (exact match, case-sensitive). Movie doc fields seen: `genres`/`cast` are arrays, `awards`/`imdb` are embedded objects.

## Current position
- **Start next session with:** finish `practice/03-mongosh.js` (random movie title via `load()`; adapt the course's getSiblingDB + `$sample` script). Stopped there: tired, said "idk" on which database/collection. Go slow: big picture (cluster → database → collection) first, using their own prompt + `show collections`. Then the next lesson.

## Topics
⬜ not started · 🟨 in progress · ✅ mastered

| # | Topic | Status |
|---|---|---|
| 1 | What MongoDB is | 🟨 |
| 2 | Setup: Atlas / local, mongosh, Compass | 🟨 (Atlas M0 cluster ✅, mongosh installed + connected ✅; Compass not yet) |
| 3 | Databases, collections, documents, `_id` | 🟨 (hierarchy, browsing, JSON vs BSON, BSON types, `_id`/ObjectId) |
| 4 | CRUD | 🟨 (insert in Atlas UI; `insertOne` + `find` in mongosh) |
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
- IP Access List: "idk" on 2026-11-15 when tired, answered correctly the next day after creating the cluster, but in the end-of-unit check forgot it again (said only username + password) until nudged. 2026-11-21: answered timeout → IP / Network Access and auth failed → password/user **without hints** ✅. Quiz once more later, then consider it solid.
- Prefers a very simple explanation of each lesson first, then check questions.
- BSON types: said "idk" on why `released` shows as `ISODate(...)`; unclear on why a DB needs a Date type. Explained (JSON has no dates, strings can't be compared/sorted as dates). Re-quiz.
- 2026-11-21 recap: forgot array match (said not found), Date reason (said "more precise"; got to compare/calculate with a hint), and the IP list again (got it with a clearer question). Said "I don't understand": the questions were unclear. **Ask recap questions concretely (show the document, split into steps).**
- Embed vs reference: for unbounded growth (50k comments) said "embed, but reference as it grows". Decide up front based on possible growth, since switching later means rewriting data + code. Re-quiz.
- Database vs collection names got mixed up when tired at the end of a long session (said "movies database"). Recheck calmly next time.
- **Never use `<placeholder>` brackets in commands.** They typed `use <sample_mflix>` literally (my fault). Describe fill-in parts in words instead.
- `use` on a wrong/nonexistent name gives no error; empty DBs don't appear in `show dbs`. Needed a very simple (desk/folder) explanation. Re-quiz.
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
| 2026-11-21 | Recap of unit 2 + unit 3, lesson 1: connection string | Recap (see weak spots). Connection string parts: `mongodb+srv://`, `user:password@`, host, `?options` (`w=majority` = write concern). SRV = one address → looks up all nodes, enables TLS. Found via Connect on the cluster card. Leaked → change password in Database Access. | Recap: comments→reference ✅, rest needed rephrasing/hints. Connection string check: all 3 ✅ (small precision: password is only after the colon; nodes, not clusters). |
| 2026-11-21 | Unit 3, lesson 2: mongosh | Installed mongosh on Windows (`winget install MongoDB.Shell`, not the course's Ubuntu steps), connected via Atlas Connect → Shell. Prompt parts (`[primary]`, current DB). Helpers: `db`, `show dbs`, `use`, `show collections`, `exit`. Empty DB (`test`) not listed until it has data. Skipped local ports 27017/28888. | Did all steps hands-on. Didn't remember why `test` isn't listed; needed desk/folder analogy. Typed `<sample_mflix>` with brackets (my placeholder) → saw the no-error trap for real, then fixed it. |
| 2026-11-21 | Unit 3, lesson 3: troubleshooting connections | Timeout = IP not on access list → Network Access → Add current IP. Auth failed = wrong password (case-sensitive) or user missing → Database Access. Too many connections (500 on M0) → restart app / `maxPoolSize`. Don't "allow access from anywhere". Home IP can change. Also: updated mongosh via `winget upgrade MongoDB.Shell`; Ubuntu not needed. | All 3 scenario questions ✅ without help. |
| 2026-11-21 | Unit 3, lesson 4: using mongosh | `db.collection.method()` shape, `find({ title: ... })`, `insertOne`, mongosh = JS console (functions), `load()` scripts + `db.getSiblingDB()`. Skipped: `sample_training` (not loaded), vim/`edit`, `$sample`. Course slide errors: stray `\` in array, `insertedIds` vs real `insertedId`. | Exercise: `find` (empty = not found) → `insertOne` Christmas Vacation → `find` again, `_id` matched ✅. Needed small nudges: collection name, then asked for the insert code (given). Wrote `db.movies.find({ title: "Christmas Vacation" })` on their own. Started `practice/03-mongosh.js` (file created, empty): knew field = `title`; mixed up database/collection, then "idk" → stopped (long session). |
