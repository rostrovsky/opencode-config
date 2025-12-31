---
description: Transform transcripts into high-yield exam prep material with standards-awareness.
---

# Study $ARGUMENTS

Automate the extraction of exam-relevant information from course transcripts using the `@educator` agent.

## Workflow

1.  **Analyze & Chunk** - Assess the input file ($ARGUMENTS):
    - Read the transcript file.
    - If the file is large (> 20,000 characters), split it into logical chunks of ~15,000 characters.
    - Plan the number of chunks and notify the user.

2.  **Extract (Phased)** - For each chunk:
    - Spawn `@educator` to process the chunk.
    - Use the specialized "Transcript → Exam Prep Extractor" instructions.
    - Store intermediate outputs.

3.  **Consolidate** - Merge all results:
    - If multiple chunks were processed, spawn `@educator` with the "Merge + Dedupe" protocol.
    - Provide all intermediate outputs as context for consolidation.
    - If only one chunk, proceed with the original extraction.

4.  **Finalize** - Save and report:
    - Write the final consolidated material to `$ARGUMENTS.study.md`.
    - Provide a summary of the extraction (e.g., number of standards found, number of questions generated).
    - Remind the user about the "Verification Checklist".

## Strategy

- **Precision**: Ensure the `@educator` agent adheres strictly to the "no guessing" policy.
- **Parallelism**: Process chunks in parallel using `@implementer` if applicable, or handle sequentially to maintain context if needed.
- **Domain Tuning**: If a domain is specified (e.g., `study --domain networking`), instruct `@educator` to prioritize domain-specific values like ports, flags, or protocols.

## Parameters
- `$1`: Path to the transcript file (required).
- `--domain`: Optional subject area (networking, security, cloud, etc.) to tailor the extraction.
