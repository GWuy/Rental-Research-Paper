# Figures

The paper currently uses compilable boxed placeholders, so no image file is required to build it. Replace each placeholder only after the diagram or plot matches the verified system or measured data.

1. Overall Microservices Architecture — Huy: gateway, seven service boundaries, owned data stores, and actual connections.
2. Event-Driven Rental Workflow — Duy: authoritative state transitions, synchronous calls, event publication, and consumers. Supplied as `figures/event_driven_workflow.svg` (source) and `figures/event_driven_workflow.pdf` (vector, wired into `sections/event_driven_design.tex` as `fig:workflow`).
3. Transactional Outbox Processing — Duy: local transaction, relay, broker acknowledgement, deduplication, and retry. Supplied as `figures/outbox_processing.svg` (source) and `figures/outbox_processing.pdf` (vector, wired as `fig:outbox`).
4. Deployment Topology — Duy: actual runtime instances, persistent components, and network boundaries. Supplied as `figures/deployment_topology.svg` (source) and `figures/deployment_topology.pdf` (vector, wired as `fig:deployment`).
5. Performance Evaluation — Hoang: measured throughput and API latency with run variability.
6. Failure Recovery — Hoang: measured fault and recovery timeline with invariant checks.

Use legible vector PDF figures where practical. Fit single-column figures within `\columnwidth` and check the final PDF at normal reading size. Preserve the existing figure labels when replacing placeholders.
