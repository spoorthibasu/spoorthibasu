## Spoorthi Basu

I build distributed systems and real-time data infrastructure. Kafka topics, Flink jobs,
Iceberg tables, and the APIs that read them back.

What draws me is the part of the design that decides whether the data is right.
**Exactly-once is a guarantee about processing, not about what ends up in your table**, and
plenty of systems are built as though those were the same thing. So I work out exactly when
they are not, and design the mechanism that closes the gap. An unusual thing to find fun, I
know, and I have yet to turn down a chance to talk about it.

Chasing it is how I ended up an **Apache Flink CDC** contributor, an **InfoQ** author, a
speaker at **Data Streaming Summit** this October, and a person who writes research papers
entirely unprompted. The Lean proofs are in
[mor-faithfulness](https://github.com/spoorthibasu/mor-faithfulness). I keep pulling on the
same thread, and it keeps going somewhere new.

### Right now

**Speaking at [Data Streaming Summit 2026](https://datastreaming-summit.org/)** in San
Francisco, October 7 and 8, on *Your Agent's Memory Is Only as Good as the Pipeline Behind
It*. The short version: durable agent memory is a CDC problem wearing new clothes, and an
agent does not crash on wrong memory. It answers confidently.

### Apache Flink CDC

[FLINK-38450](https://github.com/apache/flink-cdc/pull/4360). Duplicate records reaching
the Iceberg sink when a schema change splits writes within a checkpoint. Diagnosed and
fixed. **Merged, shipping in cdc-3.7.0.**

[FLINK-39775](https://github.com/apache/flink-cdc/pull/4418). Releasing snapshot split
metadata once the reader enters the stream phase. Large MySQL tables were holding onto
hundreds of thousands of splits and putting the JobManager on the floor. Open, in review.

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
