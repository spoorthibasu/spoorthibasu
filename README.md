## Spoorthi Basu

I build distributed systems and real-time data infrastructure. Kafka topics, Flink jobs,
Iceberg tables, and the APIs that read them back.

What draws me is the part of the design that decides whether the data is right.
**Exactly-once is a guarantee about processing, not about what ends up in your table**, and
plenty of systems are built as though those were the same thing. So I work out exactly when
they are not, and design the mechanism that closes the gap. An unusual thing to find fun, I
know, and I have yet to turn down a chance to talk about it.

Chasing it is how I ended up an **Apache Flink CDC** contributor, an **InfoQ** author, a
**Data Streaming Summit** speaker, and a person who writes research papers entirely
unprompted. I keep pulling on the same thread, and it keeps going somewhere new.

### Speaking

**[Data Streaming Summit 2026](https://datastreaming-summit.org/dss2026)**, San Francisco, in
October, on *Your Agent's Memory Is Only as Good as the Pipeline Behind It*. The short
version: durable agent memory is a CDC problem wearing new clothes, and an agent does not
crash on wrong memory. It answers confidently.

### Apache Flink CDC

Two threads, both about what ends up in the table.

**Correctness.** Duplicate records were reaching the Iceberg sink when a schema change split
writes within a checkpoint. Exactly-once said everything was fine. Diagnosed and fixed.

**Memory.** The source coordinator kept every finished snapshot split for the life of the job
and re-serialized all of it on each checkpoint. A 2.5B-row MySQL table meant ~300K splits and
a JobManager on the floor. I added an opt-in release once the reader enters the stream phase:
first for MySQL, then generalized into flink-cdc-base so Postgres, SQL Server, Oracle, Db2,
and MongoDB get it. That covers every source connector with incremental snapshots.

Merged work was released in
[cdc-3.7.0](https://flink.apache.org/2026/10/10/apache-flink-cdc-3.7.0-release-announcement/).
The full list, open and merged, is
[here](https://github.com/apache/flink-cdc/pulls?q=is%3Apr+author%3Aspoorthibasu).

### Writing

[Schema Proliferation in Kafka and Flink Pipelines](https://www.infoq.com/articles/schema-proliferation-problem/).
**InfoQ**, 2026. **Top article in that week's round-up.** Twelve schemas collapsed into one
discriminator-based record, so one filtered query works where twelve used to.

### Under review

*Audit-Preserving Compaction for Merge-on-Read Tables*, at PVLDB. Compacting a
merge-on-read table discards the evidence of whether the current row per key was ever
correct. This keeps it. Companion artifact:
[mor-faithfulness](https://github.com/spoorthibasu/mor-faithfulness).

*The History Was Already There*, at CACM Practice. Rebuilding old values from an
append-only audit trail instead of storing previous-value columns. Companion artifact:
[kafka-flink-audit-trail](https://github.com/spoorthibasu/kafka-flink-audit-trail).

More at [spoorthibasu.github.io](https://spoorthibasu.github.io).
