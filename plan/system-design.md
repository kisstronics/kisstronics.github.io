<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# provide a 3 months plan for system design to cover all the topics with detailed plan

Here’s a **detailed 3‑month system design plan** that takes you from fundamentals to advanced distributed systems and real‑world architectures, with a strong focus on **backend / AWS / microservices** (aligned with your background).[^1][^2][^3][^4][^5]

***

## How to Use This Plan

- **Time**: ~2–3 hours/day on weekdays, 4–6 hours on weekends.
- **Goal**: Be able to:
    - Design scalable, reliable systems end‑to‑end.
    - Talk confidently about trade‑offs (DB choice, consistency, scaling, failures).
    - Handle typical senior/lead system design interviews.
- **Output**:
    - A personal “System Design Playbook” (notes + diagrams).
    - 15–20 practiced designs (URL shortener → Instagram → Uber → etc.).
    - A set of reusable architecture patterns for your own projects.[^2][^5]

***

## Month 1 – Foundations \& Core Building Blocks

Focus: Build solid mental models for **scalability, availability, latency**, and the main components (LB, cache, DB, queue, API).

### Week 1 – System Design Fundamentals

**Day 1 – What Is System Design?**

- Learn: HLD vs LLD, functional vs non‑functional requirements (NFRs).
- Practice: For 2 apps you know well, write:
    - Functional requirements.
    - NFRs: latency, availability, scalability, security, cost.[^4][^1]

**Day 2 – Performance Basics**

- Learn: Latency, throughput, bandwidth, response time, p50/p95/p99.
- Practice: Estimate latency for:
    - A simple API call.
    - A DB read/write.
    - A cached read.
- Deliverable: 1‑page notes on performance metrics.

**Day 3 – Scalability \& Capacity Planning**

- Learn: Vertical vs horizontal scaling.
- Learn: Basic capacity estimation (requests/sec, storage, bandwidth).
- Practice: Back‑of‑envelope for:
    - 1M DAU, 10 requests/user/day.
    - 100GB/day log ingestion.[^1][^4]

**Day 4 – Availability \& Reliability**

- Learn: Availability (% uptime), SLO/SLI/SLA concepts.
- Learn: Redundancy, replication, failover, single point of failure (SPOF).
- Practice: For a simple web app, identify SPOFs and how to remove them.[^6][^7]

**Day 5 – Back‑of‑Envelope Estimation**

- Learn: Quick math for:
    - Storage, QPS, bandwidth.
- Practice: Estimate for:
    - URL shortener.
    - Chat app (messages/day, storage/month).[^5][^2]

**Day 6 – System Design Process**

- Learn: Standard interview/design flow:

1. Clarify requirements.
2. Estimate scale.
3. Define APIs \& data model.
4. High‑level design.
5. Deep dive (DB, cache, scaling).
6. Bottlenecks \& improvements.[^5][^1]
- Deliverable: A 1‑page checklist you’ll reuse for every design.

**Day 7 – Review \& Mini‑Design**

- Design: **URL Shortener** (tiny URL) at a high level.
- Use your checklist; draw a simple HLD diagram.[^4]

***

### Week 2 – Networking, APIs, and Traffic Management

**Day 8 – Networking Essentials**

- Learn: TCP/IP, HTTP/HTTPS, TLS, DNS, CDN basics.
- Practice: Trace a request from browser → LB → service → DB.
- Notes: Latency contributors at each hop.[^3][^4]

**Day 9 – REST API Design**

- Learn: Resources, verbs, status codes, versioning, pagination, filtering.
- Practice: Design REST APIs for:
    - Users, posts, comments.
    - Orders, products, carts.[^3][^6]

**Day 10 – RPC, gRPC, GraphQL**

- Learn: REST vs RPC vs gRPC vs GraphQL trade‑offs.
- Practice: Pick scenarios where each is ideal (e.g., internal microservices → gRPC, public flexible queries → GraphQL).[^3][^4]

**Day 11 – Load Balancing**

- Learn: L4 vs L7 LB, round‑robin, least connections, IP hash, sticky sessions.
- Learn: LB as reverse proxy, health checks.
- Practice: Design LB layer for a stateless API cluster.[^8][^1]

**Day 12 – API Gateway \& BFF**

- Learn: API Gateway roles (auth, rate limit, routing, aggregation).
- Learn: Backend‑for‑Frontend (BFF) pattern.
- Practice: Design gateway for web + mobile clients with different needs.[^8][^1]

**Day 13 – Rate Limiting \& Throttling**

- Learn: Rate limit algorithms (fixed window, sliding log, token bucket, leaky bucket).
- Learn: Where to enforce (LB, gateway, service).
- Practice: Design rate limiter for a public API.[^6][^3]

**Day 14 – Mini‑Design: API Platform**

- Design: A **public API platform** (like a small Stripe‑style API):
    - LB + API Gateway + services + rate limiting + auth.
- Document: APIs, components, scaling approach.[^8]

***

### Week 3 – Databases \& Storage

**Day 15 – Relational DB Fundamentals**

- Learn: Tables, indexes, normalization (up to 3NF/BCNF), ACID.
- Practice: Model schema for:
    - E‑commerce (users, products, orders).
    - Blog (users, posts, comments).[^6][^3]

**Day 16 – Indexing \& Query Performance**

- Learn: B‑tree indexes, composite indexes, covering indexes.
- Learn: EXPLAIN plans (conceptually).
- Practice: For 3 queries, decide which indexes to add and why.[^3][^6]

**Day 17 – NoSQL Overview**

- Learn: Key‑value, document, wide‑column, graph DBs.
- Learn: When to choose SQL vs NoSQL.
- Practice: Pick DB types for:
    - Session store.
    - Activity feed.
    - Social graph.[^4][^6]

**Day 18 – Scaling Databases**

- Learn: Read replicas, master‑slave, master‑master.
- Learn: Sharding, partitioning strategies (range, hash, directory).
- Practice: Design sharded user table (by user_id, region, etc.).[^6][^3]

**Day 19 – Consistency \& Transactions**

- Learn: Strong vs eventual consistency.
- Learn: CAP theorem, PACELC (conceptual).
- Learn: Distributed transaction patterns (2PC, SAGA, outbox).[^3][^6]
- Practice: For an order + payment + inventory flow, sketch a SAGA.

**Day 20 – Object Storage \& CDN**

- Learn: S3‑style object storage, presigned URLs.
- Learn: CDN for static assets, caching behavior.
- Practice: Design storage + CDN for:
    - Profile images.
    - Video uploads (high‑level).[^4][^8]

**Day 21 – Mini‑Design: Data Layer for E‑Commerce**

- Design: DB + storage layer for an e‑commerce site:
    - SQL for core, NoSQL for sessions/cart, S3 + CDN for images.
- Document: Schema, scaling, consistency choices.[^4]

***

### Week 4 – Caching, Queues, and Async Patterns

**Day 22 – Caching Fundamentals**

- Learn: Where to cache (client, CDN, LB, service, DB).
- Learn: Cache eviction (LRU, LFU, TTL).
- Practice: For a news site, define cache layers and TTLs.[^8][^6]

**Day 23 – Caching Strategies**

- Learn: Cache‑aside, read‑through, write‑through, write‑behind, write‑invalidate.
- Practice: Choose strategies for:
    - User profile service.
    - Product catalog.[^6][^3]

**Day 24 – Message Queues \& Pub/Sub**

- Learn: Queue vs pub/sub, at‑most/once/at‑least/exactly‑once semantics.
- Learn: Kafka, SQS, RabbitMQ (conceptual roles).
- Practice: Use cases for:
    - Email sending.
    - Analytics events.
    - Order processing.[^3][^4]

**Day 25 – Async Processing \& Workflows**

- Learn: Background jobs, workers, retries, dead‑letter queues.
- Practice: Design async workflow for:
    - Image processing (upload → thumbnail generation).
    - Report generation.[^4]

**Day 26 – Idempotency \& Deduplication**

- Learn: Idempotent operations, idempotency keys.
- Practice: Design idempotent payment charge API.[^6][^3]

**Day 27 – Event‑Driven Patterns**

- Learn: Event sourcing, CQRS (conceptual).
- Practice: Sketch CQRS for:
    - Order read model vs write model.[^7][^4]

**Day 28 – Mini‑Design: Feed / Notification System**

- Design: A notification system (email + push + in‑app):
    - API → queue → workers → providers.
    - Caching for user preferences.
- Document: Flow, retry strategy, idempotency.[^4]

***

## Month 2 – Distributed Systems \& Advanced Patterns

Focus: Handle **failures, consistency, and scale** with distributed patterns; learn common architectures (microservices, event‑driven, real‑time).

### Week 5 – Distributed Systems Core

**Day 29 – Distributed System Challenges**

- Learn: Network partitions, latency, clock skew, partial failures.
- Notes: How these affect your designs.[^7][^3]

**Day 30 – CAP \& Consistency Models**

- Revisit CAP deeply; add BASE.
- Learn: Strong, eventual, causal consistency.
- Practice: For 3 systems, decide acceptable consistency level and why.[^3][^6]

**Day 31 – Replication \& Leader Election**

- Learn: Leader‑follower, multi‑leader, leaderless.
- Learn: Leader election, heartbeats (conceptual).
- Practice: How your DB cluster handles leader failure.[^7][^3]

**Day 32 – Partitioning \& Consistent Hashing**

- Learn: Consistent hashing, virtual nodes.
- Practice: Design consistent hashing for:
    - Cache cluster.
    - Sharded key‑value store.[^6][^3]

**Day 33 – Distributed Transactions**

- Learn: 2PC, SAGA (choreography vs orchestration), outbox pattern, CDC.
- Practice: Re‑design order + payment + inventory with:
    - SAGA + outbox.[^3][^4]

**Day 34 – Quorum \& Consensus (Conceptual)**

- Learn: Quorum reads/writes, Paxos/Raft (high‑level).
- Notes: Where you’d rely on managed services vs implementing yourself.[^7][^3]

**Day 35 – Mini‑Design: Globally Distributed KV Store (HLD)**

- Design: High‑level design for a simple key‑value store:
    - Partitioning, replication, consistency, failure handling.
- Keep it conceptual; focus on trade‑offs.[^3]

***

### Week 6 – Microservices \& Service Communication

**Day 36 – Monolith vs Microservices**

- Learn: Pros/cons, when to split.
- Practice: For an existing monolith you know, propose service boundaries.[^1][^4]

**Day 37 – Service Boundaries \& Domain Modeling**

- Learn: Bounded contexts, domain‑driven design (high‑level).
- Practice: Define services for:
    - E‑commerce (catalog, orders, payments, users, notifications).[^4]

**Day 38 – Service Communication Patterns**

- Learn: Sync (HTTP/gRPC) vs async (events).
- Learn: Request‑response, publish‑subscribe, fan‑out.
- Practice: Choose patterns for inter‑service calls in your e‑commerce design.[^8][^3]

**Day 39 – Service Discovery \& Config**

- Learn: Service registry, DNS‑based discovery, sidecars (conceptual).
- Learn: Centralized config vs env vars.
- Practice: How your services find each other in AWS (ALB + target groups, service discovery).[^4]

**Day 40 – Resilience Patterns**

- Learn: Retries with backoff, circuit breakers, bulkheads, timeouts, fallbacks.
- Practice: Add resilience to:
    - Payment service calling external gateway.
    - Inventory service calling DB.[^8][^3]

**Day 41 – API Gateway in Microservices**

- Revisit API Gateway:
    - Auth, routing, aggregation, rate limiting, logging.
- Practice: Design gateway for your microservices architecture.[^1][^8]

**Day 42 – Mini‑Design: Microservices E‑Commerce**

- Design: Full microservices architecture for e‑commerce:
    - Services, DBs, caches, queues, gateway.
    - Resilience patterns, scaling.
- Document: Data flow for “place order”.[^4]

***

### Week 7 – Real‑Time, Streaming, and Data‑Intensive Systems

**Day 43 – Real‑Time Communication**

- Learn: WebSockets, SSE, long polling.
- Practice: When to use each (chat, live updates, notifications).[^6][^4]

**Day 44 – Chat \& Presence System**

- Learn: Connection management, fan‑out, message storage.
- Practice: Design a 1‑to‑1 chat system:
    - WS servers, message queue, DB for history.[^4]

**Day 45 – Stream Processing Basics**

- Learn: Batch vs stream, event time vs processing time.
- Learn: Kafka streams / Flink‑style concepts (high‑level).
- Practice: Use cases for:
    - Real‑time analytics.
    - Fraud detection.[^3][^4]

**Day 46 – Data Pipelines \& ETL**

- Learn: Ingestion → transform → load, data lakes/warehouses (conceptual).
- Practice: Design pipeline for:
    - Clickstream → analytics DB.[^9][^4]

**Day 47 – Search Systems**

- Learn: Inverted index, tokenization, relevance scoring (high‑level).
- Learn: Elasticsearch/OpenSearch‑style architecture.
- Practice: Design search for:
    - Products.
    - Posts/articles.[^4]

**Day 48 – Recommendation Systems (High‑Level)**

- Learn: Collaborative filtering, content‑based (conceptual).
- Learn: Offline batch vs online real‑time recommendations.
- Practice: High‑level design for a “recommended for you” feature.[^4]

**Day 49 – Mini‑Design: Real‑Time Analytics Dashboard**

- Design: System that shows:
    - Live DAU, events/sec, top pages.
- Include: Ingestion, stream processing, storage, serving layer.[^4]

***

### Week 8 – Security, Observability, and Reliability

**Day 50 – Security Fundamentals**

- Learn: AuthN vs AuthZ, sessions vs JWT, OAuth2/OIDC (high‑level).
- Practice: Design auth for:
    - Web + mobile app with social login.[^6][^3]

**Day 51 – API Security**

- Learn: TLS, mTLS (conceptual), input validation, rate limiting, WAF.
- Practice: Secure your public API design from Week 2.[^8][^3]

**Day 52 – Observability: Logging, Metrics, Tracing**

- Learn: Centralized logging, structured logs.
- Learn: Metrics (counters, gauges, histograms), dashboards.
- Learn: Distributed tracing (spans, trace IDs).[^7][^3]

**Day 53 – Monitoring \& Alerting**

- Learn: SLIs/SLOs, error budgets.
- Learn: Alerting strategies (symptom‑based, not cause‑based).
- Practice: Define 3–5 key SLOs for your e‑commerce system.[^7][^3]

**Day 54 – Reliability \& DR**

- Learn: Multi‑AZ, multi‑region, active‑passive vs active‑active.
- Learn: Backup strategies, RPO/RTO.
- Practice: DR plan for your main app (region failure).[^7][^4]

**Day 55 – Cost \& Trade‑Off Thinking**

- Learn: Cost drivers (compute, storage, data transfer).
- Practice: For two designs, estimate rough monthly cost and discuss trade‑offs.[^9][^7]

**Day 56 – Review \& Consolidation**

- Revisit your playbook:
    - Add sections: Security checklist, Observability checklist, DR checklist.
- Refine 2–3 earlier designs with these new concerns.[^7]

**Day 57 – Mini‑Design: Secure, Observable Microservices Platform**

- Design: A platform hosting multiple microservices:
    - Auth, gateway, services, observability stack, alerts, DR.
- Document: How you’d operate it day‑to‑day.[^8][^7]

***

## Month 3 – Applied System Design \& Interview Mastery

Focus: Practice **real‑world designs** end‑to‑end, refine your approach, and simulate interviews.

### Week 9 – Classic Interview Designs I

**Day 58 – Design: Rate‑Limited Key‑Value Store**

- Requirements: High QPS, TTL, rate limiting per key.
- Design: API, data model, sharding, caching, rate limiting.[^4]

**Day 59 – Design: Pastebin / Code Sharing**

- Focus: Storage, sharing links, code highlighting (high‑level), abuse prevention.[^4]

**Day 60 – Design: Web Crawler**

- Focus: URL frontier, politeness, deduplication (Bloom filters), storage.[^4]

**Day 61 – Design: Analytics Event Collector**

- Focus: High write throughput, batching, partitioning, late events.[^4]

**Day 62 – Design: File Storage (Dropbox‑Lite)**

- Focus: Chunking, deduplication, metadata DB, sync clients (high‑level).[^4]

**Day 63 – Deep Dive: Refine 2 Designs**

- Pick 2 from this week.
- Add: Failure scenarios, scaling limits, observability.

**Day 64 – Mock Design Session (Self)**

- Simulate 45‑min interview:
    - Pick a new problem (e.g., “Design a metrics dashboard”).
    - Follow your checklist strictly.
- Record your diagram + notes.[^5]

***

### Week 10 – Classic Interview Designs II

**Day 65 – Design: Social News Feed (Twitter‑Lite)**

- Focus: Feed generation (pull vs push), fan‑out, caching.[^1][^4]

**Day 66 – Design: Photo Sharing (Instagram‑Lite)**

- Focus: Media upload, CDN, feed, likes/comments.[^1][^4]

**Day 67 – Design: Chat System (WhatsApp‑Lite)**

- Focus: 1‑to‑1 + group chat, presence, message ordering, offline.[^4]

**Day 68 – Design: Ride‑Sharing (Uber‑Lite)**

- Focus: Location tracking, matching, pricing (high‑level), payments.[^1][^4]

**Day 69 – Design: Video Streaming (YouTube‑Lite)**

- Focus: Upload, transcoding, CDN, playback, recommendations (high‑level).[^4]

**Day 70 – Deep Dive: Refine 2 Designs**

- Add:
    - Multi‑region considerations.
    - Back‑of‑envelope numbers.

**Day 71 – Mock Design Session (Peer or Self)**

- Do another 45‑min mock with a different problem (e.g., “Design a food delivery system”).[^5]

***

### Week 11 – Domain‑Specific \& Advanced Designs

**Day 72 – Design: E‑Commerce Platform (Full)**

- End‑to‑end:
    - Catalog, search, cart, orders, payments, notifications.
    - Microservices, DBs, caches, queues.[^4]

**Day 73 – Design: Ticket Booking (BookMyShow‑Lite)**

- Focus: Seat locking, concurrency, payments, high load during sales.[^1]

**Day 74 – Design: Maps / Location Service (Google Maps‑Lite)**

- Focus: Geohashing, nearest neighbors, routing (high‑level).[^1][^6]

**Day 75 – Design: Collaboration Tool (Google Docs‑Lite)**

- Focus: Real‑time edits, conflict resolution (CRDT/operational transforms high‑level).[^4]

**Day 76 – Design: Ad‑Tech / Real‑Time Bidding (High‑Level)**

- Focus: Low latency, auctions, tracking, privacy (conceptual).[^4]

**Day 77 – Deep Dive: Your Own Domain**

- Pick a system from your work (e.g., “Distributed Job Scheduler”).
- Design it properly using everything you’ve learned.

**Day 78 – Mock Design Session (Timed + Written)**

- 45‑min mock + write‑up:
    - Problem statement.
    - Requirements, HLD, DB, scaling, trade‑offs.[^5]

***

### Week 12 – Interview Prep, Patterns, and Playbook Finalization

**Day 79 – Pattern Review: Scaling Reads**

- Revisit:
    - Caching layers, read replicas, CDN, precomputation.
- Summarize as a reusable pattern card.[^7]

**Day 80 – Pattern Review: Scaling Writes**

- Revisit:
    - Sharding, queues, async processing, backpressure.
- Summarize as a pattern card.[^7]

**Day 81 – Pattern Review: Consistency \& Transactions**

- Revisit:
    - SAGA, outbox, idempotency, eventual consistency patterns.
- Summarize as a pattern card.[^3]

**Day 82 – Pattern Review: Failure \& Resilience**

- Revisit:
    - Retries, circuit breakers, bulkheads, fallbacks, DR.
- Summarize as a pattern card.[^8][^3]

**Day 83 – Full Mock Interview 1**

- 45‑min design + 15‑min reflection.
- Use a new problem you haven’t designed before.[^5]

**Day 84 – Full Mock Interview 2**

- Another 45‑min design with strict timing.
- Focus on:
    - Clear communication.
    - Explicit trade‑offs.
    - Driving the conversation.[^5]

**Day 85 – Playbook Finalization**

- Consolidate:
    - Checklists (requirements, estimation, components, failure, security, observability).
    - Pattern cards.
    - 10–15 polished designs with diagrams.
- Write a 1–2 page “How I Approach Any System Design” summary.[^5]

**Day 86–89 – Targeted Revision**

- Revisit weak areas:
    - E.g., consistency models, real‑time systems, or specific designs.
- Re‑draw 3–5 key diagrams from memory.

**Day 90 – Final Review \& Next Steps**

- Do one last mock (optional).
- Define:
    - What to practice monthly to keep sharp.
    - 2–3 advanced topics to dive deeper (e.g., Kubernetes architecture, advanced streaming, multi‑region active‑active).[^7]

***

## Suggested Resources

Use these alongside your daily work:

- **System Design Handbooks \& Roadmaps**
    - System Design Handbook roadmap (phases, patterns).[^2]
    - Backend Engineering roadmaps (system design sections).[^10][^3]
- **Articles \& Blogs**
    - High‑level system design roadmaps for backend engineers.[^1][^4]
    - Distributed systems, microservices, observability articles.[^8][^7]
- **Practice**
    - Common interview designs: URL shortener, feed, chat, Uber, Instagram, ticket booking, maps, etc.[^1][^4]

***

If you want, I can turn this into a **checklist file** (Markdown) with checkboxes for each day so you can track progress in a repo, similar to the SQL plan.
<span style="display:none">[^11][^12][^13][^14][^15]</span>

<div align="center">⁂</div>

[^1]: https://www.youtube.com/watch?v=eGWZoupD-eM

[^2]: https://www.systemdesignhandbook.com/guides/system-design-roadmap/

[^3]: https://backend-engineering-roadmaps.vercel.app/docs/core-cs/system-design-roadmap

[^4]: https://www.hungrycoders.com/blog/system-design-roadmap-from-basics-to-advanced

[^5]: https://designgurus.substack.com/p/system-design-learning-path-what

[^6]: https://www.linkedin.com/posts/satyamparmar_systemdesign-softwareengineering-backenddevelopment-activity-7400714543984939008-cnch

[^7]: https://www.linkedin.com/pulse/mastering-system-design-practical-roadmap-every-akshay-kanherkar-0cwxf

[^8]: https://www.linkedin.com/posts/abhishek-chatrath1_linkedin-cybersecurity-cloudsecurity-activity-7412501356659298304-dheY

[^9]: https://www.linkedin.com/posts/goyalshalini_want-to-master-system-design-but-dont-know-activity-7368168288037601280-MczM

[^10]: https://roadmap.sh/system-design

[^11]: https://www.scribd.com/document/947786787/System-Design-3Month-12Week-Plan

[^12]: https://www.youtube.com/watch?v=byUFmW0ufts

[^13]: https://www.geeksforgeeks.org/system-design/complete-roadmap-to-learn-system-design/

[^14]: https://www.youtube.com/watch?v=7YGE_xeb5ZQ

[^15]: https://hellonehha.medium.com/system-design-roadmap-for-beginners-b06056f77cba

