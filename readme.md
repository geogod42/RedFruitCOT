# RedFruitCOT

A speculative attempt at reverse-engineering OpenAI's "Strawberry" (now o1) before its public release. Built on September 11, 2024 — one day before o1-preview was announced.

The idea: if you make an LLM spend more compute at inference time by critiquing and refining its own outputs, you get better answers. This implements a generate → critique → grade → refine loop using Llama 3.1 70B on AWS Bedrock.

## How It Works

1. **Generate** 3 independent candidate answers to a prompt
2. **Critique** each answer using the same LLM
3. **Grade** each on a -100 to 100 scale based on the critique
4. **Select** the best, **refine** it
5. **Repeat** for N iterations

## Usage

Requires `boto3` and AWS CLI credentials configured.

```sh
python3 redfruit.py
```

Convert the output to readable HTML:

```sh
python3 htmlize.py
```
