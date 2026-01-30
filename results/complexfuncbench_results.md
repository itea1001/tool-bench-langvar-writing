# ComplexFuncBench Language Variation Results

## Main Results

### gpt-4.1-mini

| Language | Accuracy | Notes |
|----------|----------|-------|
| English (en) | 86.4% | Baseline |
| Chinese (zh) | 86.0% | Matches English |
| French (fr) | 82.0% | |
| Swahili (sw) | 81.8% | Low-resource, surprisingly good |
| Vietnamese (vi) | 69.0% | |
| Spanish (es) | 64.0% | Unexpected drop for high-resource lang |

### gpt-4.1

| Language | Accuracy | Notes |
|----------|----------|-------|
| English (en) | 86.4% | Baseline |
| Vietnamese (vi) | 86.0% | Recovered on larger model |
| Swahili (sw) | 86.4% | Matches English |
| Spanish (es) | 68.0% | Still lower than expected |

## Tool Doc Translation Results

When tool documentation (function descriptions, parameter descriptions) is also translated:

| Language | gpt-4.1-mini | Notes |
|----------|--------------|-------|
| Spanish (es) | 63.6% | Dropped from 64% baseline |
| Swahili (sw) | 86.4% | Improved to match English |
| Chinese (zh) | 86.0% | Unchanged |

## Nonsense Description Experiment

Replaced tool descriptions with lorem ipsum text while keeping function names unchanged:

| Model | Baseline | Nonsense Descriptions |
|-------|----------|----------------------|
| gpt-4.1-mini | 86.4% | 86.4% |
| gpt-4.1 | 86.4% | 86.4% |

**Key Finding**: Models achieve identical accuracy with nonsense descriptions, suggesting they rely primarily on function names rather than descriptions for tool selection. This confirms findings from [Hypogenic AI's mechanistic interpretability research](https://github.com/Hypogenic-AI/mechanistic-llm-tools-claude).

## Open Questions

1. Why does Spanish show such a large drop despite being a high-resource language?
2. Is this pattern GPT-specific or does it generalize to Claude/Llama?
3. If models don't read descriptions, why does translating them sometimes affect performance?
