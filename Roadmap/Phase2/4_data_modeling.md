# Data modeling, performance and reliability

First principle: data architecture is about making the right facts accessible at an acceptable cost, with known guarantees.

Learn:
- Star schema versus one big table.
- Facts, dimensions and slowly changing dimensions.
- Partitioning, clustering and indexing.
- Query plans and performance bottlenecks.
- Data skew, memory limits and distributed processing fundamentals.
- Data-quality tests, alerting and pipeline observability.
- When Spark is needed versus when a local database is sufficient.


Hands-on lab: 
- create an analytics pipeline that calculates ticket volume, customer retention, SLA compliance and support workload.
- Compare a slow query with an optimized query. Record the execution plan and measured improvement rather than claiming performance gains without evidence.
- Checkpoint: explain what happens when a client changes a schema, sends duplicate records, or delivers yesterday's data instead of today's.