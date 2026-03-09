# Evaluation and Benchmarks

## Loss-Based Evaluation

## Example Benchmarks
MMLU
HumanEval
GSM8k

## Properties of good benchmarks
- Breadth / diversity: evaluates all desired input-output functionality
- Depth / difficulty: Examples are difficult enough to distinguish good and bad models
- Utility: Task is a proxy for desired functionality
- Robustness: robustness to input variations
- Data (un-)contamination
- Efficient to evaluate


## Automatically evaluating complex text
- word overlap:
    Rough: Count the word overlap between the prediction & ref.answer
- use a LLM ("LLM as a judge")
- use humans