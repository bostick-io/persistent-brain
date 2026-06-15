# Decisions

Choices made on purpose, with the reasoning, so they do not get relitigated every week.

## Postgres over a document store

The data is relational and the queries are mostly joins and aggregates. A document store
would have meant hand-rolling those joins. Revisit only if the data shape changes.

## Daily email digest, not real-time push

A once-a-day digest was chosen over per-event notifications. At this scale it is simpler
and far less noisy for users. Real-time push can come later if people ask for it.
