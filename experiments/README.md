# Experiment records

Owner: Hoang. No measurements have been performed for this paper template.

Before each run, record the source revision, service and dependency versions, hardware, network, PostgreSQL and Kafka configuration, test data seed, workload mix, offered rate, warm-up, measurement window, and repetition number. Keep scripts and non-sensitive configuration under version control. Keep raw logs and result files in `experiments/raw/` and `experiments/results/`; these directories are ignored by default because outputs may be large or sensitive. Provide a reproducible way to retrieve or regenerate any data used in the paper.

Planned trials: API throughput and latency; Kafka publication and consumption lag; duplicate-event replay; service interruption and recovery; outbox relay interruption at each relevant crash point. For every trial, specify the expected invariant, exact fault-injection point, observation interval, and pass/fail rule before inspecting results. Retain unsuccessful trials. Never insert a synthetic or estimated result into the paper as a measurement.
