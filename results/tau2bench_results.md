# tau2-bench Language Variation Results

## Methodology

For tau2-bench, we modified the user simulator to speak in the target language by adding language instructions to the system prompt: "You MUST respond in {language} only".

## tau2-airline Results (50 tasks)

### gpt-4.1-mini (agent and user simulator)

| Language | Accuracy | Δ from EN |
|----------|----------|-----------|
| English (en) | 48% | - |
| Chinese (zh) | 40% | -8% |
| Spanish (es) | 32% | -16% |
| Swahili (sw) | 30% | -18% |

### gpt-4.1 agent (gpt-4.1 user simulator)

| Language | Accuracy | Δ from EN |
|----------|----------|-----------|
| English (en) | 60% | - |
| Chinese (zh) | 54% | -6% |
| Swahili (sw) | 48% | -12% |
| Spanish (es) | 46% | -14% |

### claude-sonnet-4.5 agent (gpt-4.1 user simulator)

| Language | Accuracy | Δ from EN |
|----------|----------|-----------|
| Chinese (zh) | 56% | +6% |
| English (en) | 50% | - |
| Swahili (sw) | 46% | -4% |
| Spanish (es) | 40% | -10% |

## Key Observations

1. **Spanish consistently underperforms** across all agent models (~10-16% below English)
2. **Chinese performs relatively well** - sometimes matching or exceeding English (claude-sonnet)
3. **Stronger models reduce the gap** - gpt-4.1 shows smaller language gaps than gpt-4.1-mini
4. **Claude does better on Chinese** than GPT models

## Error Analysis

Comparing EN success vs ES failure cases for claude-sonnet on airline:

**Failure Modes:**
1. **Policy hallucination** - model makes up different rules in Spanish (e.g., "can only offer certificate when passenger wants to cancel")
2. **Premature task completion** - claims success but DB state is wrong
3. **Earlier give-up** - more likely to transfer to human agent in Spanish
4. **Identifier extraction issues** - model confused about user_id vs name in non-English conversations

**User Simulator Confound:**
The user simulator generates different information patterns in different languages. In English it might say "my user ID is mei_brown_7075" but in Spanish just "Hola, soy Mei Brown" without the user_id.
