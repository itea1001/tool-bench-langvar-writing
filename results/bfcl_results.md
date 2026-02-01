# BFCL Language Variation Results

## Translation Approach

For BFCL, we translate:
1. User queries (questions)
2. System prompts
3. Function descriptions (optional, with `--translate-tool-docs` flag)

**Not translated** (kept in English):
- Function names
- Parameter names
- Parameter types

## Single-Turn Results

*Results pending - experiments in progress*

## Multi-Turn Results

The `translate_bfcl.py` script handles multi-turn by iterating through each turn and translating user messages via `translate_question()` function.

*Results pending - experiments in progress*

## Notes

BFCL uses a different evaluation paradigm than tau2-bench:
- tau2-bench: agentic with user simulator
- BFCL: direct function calling without multi-turn simulation

This may lead to different language variation patterns.
