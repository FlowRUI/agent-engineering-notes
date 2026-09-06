# Retrieval-Augmented Generation

RAG is an evidence-routing system, not merely a vector search call.

## Retrieval pipeline

```mermaid
flowchart LR
  Q[Question] --> I[Intent & scope]
  I --> C[Candidate retrieval]
  C --> R[Reranking]
  R --> W[Evidence window]
  W --> A[Answer with citations]
  A --> E[Retrieval & answer evaluation]
```

## Design decisions

| Decision | Question |
| --- | --- |
| Chunking | What semantic unit should remain intact? |
| Indexing | Which metadata is required for filtering and provenance? |
| Query rewriting | Does the rewrite preserve user intent? |
| Hybrid retrieval | Which failures require lexical rather than semantic matching? |
| Reranking | What evidence deserves scarce context budget? |
| Citation | Can each claim be mapped to a retrieved source? |

## Common failure modes

- High similarity but wrong authority
- Correct source retrieved, decisive sentence truncated
- Query rewrite removes a constraint
- Duplicate chunks crowd out diverse evidence
- Answer remains fluent when evidence is insufficient

## Evaluation layers

1. **Retrieval:** recall and precision of relevant evidence.
2. **Context:** whether the selected window preserves decisive information.
3. **Grounding:** whether claims are supported by citations.
4. **Task value:** whether the answer enables the correct next action.

The system should be able to abstain or clarify when evidence is missing.
