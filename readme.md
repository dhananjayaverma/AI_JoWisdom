Part 3. Level 2 — Projects that demonstrate senior engineering
Once you can ship complete applications, move into projects that demonstrate systems thinking, reliability, and production ownership.
Project 5 — Distributed Job Queue
Priority: P1/P2

Build a small background-job processing system that can accept jobs, distribute them to workers, retry failures, and expose job status.
Stack
- Node.js and TypeScript.
- PostgreSQL for durable job state.
- Redis for coordination or queueing, depending on your design.
- Docker.
- OpenTelemetry-compatible instrumentation.
- Prometheus and Grafana if you want to demonstrate metrics.
- Vitest and integration tests.
Architecture
Producer / Client
       |
       v
Job Submission API
       |
       v
Durable Job Store / Queue
       |
       v
Worker Pool
       |
       +---- Retry Scheduler
       |
       +---- Dead-Letter Handling
       |
       +---- Metrics and Logs

Modules
- Job submission.
- Job validation.
- Queue scheduling.
- Worker registration.
- Lease or lock management.
- Retry policy.
- Dead-letter queue.
- Job cancellation.
- Job status API.
- Metrics and tracing.
Engineering questions to answer
- What happens if a worker crashes halfway through a job?
- How are stuck jobs detected?
- How do you prevent duplicate processing from causing duplicate business effects?
- How are retries delayed?
- What happens when a queue is overloaded?
- How do you shut down a worker gracefully?
For a first implementation, you can use an existing queue library. If you want to learn distributed-systems internals, build a separate educational version rather than reinventing production infrastructure for every application.