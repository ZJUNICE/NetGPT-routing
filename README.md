# Public Artifact for the Paper

This repository contains the compact public artifact accompanying paper *Optimizing NetGPT via Routing-Based Synergy and Reinforcement Learning on* LLM-based task planning and adaptive routing for federated-learning workflows. 

This release is scoped as a data and reference-code artifact. It includes the public datasets used at the main stages of the method and a small set of representative scripts for data generation, supervised fine-tuning, reward/preference training, PPO-style policy optimization, and routing-time inference.

## Relation to the Paper

The paper studies an agentic federated-learning workflow in which an LLM selects the next operation, a local model proposes candidate actions, a reward/preference model scores action quality, and a routing layer decides when to use local or cloud inference. The files in this artifact correspond to the main stages reported in the manuscript.

| Paper component | Public files | Purpose |
| --- | --- | --- |
| Task planning data generation | `scripts/data_generator_neo.py` | Generates federated-learning planning examples with task goals, completed steps, and target tool actions. |
| Supervised fine-tuning data | `datasets/sft_train.json`, `datasets/sft_test.json` | Trains and evaluates the next-action planning model. |
| Reward/preference data | `datasets/rm_train.jsonl`, `datasets/rm_test.jsonl`, | Supports reward-model training and preference-based policy optimization. |
| PPO-style policy data | `datasets/ppo_train.jsonl` | Provides policy-optimization examples derived from preference pairs. |
| Frozen evaluation set | `datasets/frozen_eval.jsonl` | Provides 1000 fixed next-action evaluation examples for stable reporting. |
| Router/classifier data | `datasets/router_classifier_train.jsonl`, `datasets/router_classifier_test.jsonl` | Trains/evaluates the lightweight routing classifier used by the adaptive inference framework. |
| Main training scripts | `scripts/SFT/finetune_test.py`, `scripts/RL/train_RM_MP.py`, `scripts/RL/train_DPO_MP.py`, `scripts/RL/train_PPO_MP.py` | Reference entry points for the training stages described in the paper. |
| Inference and routing framework | `scripts/flow_main.py`, `scripts/model_provider.py`, `scripts/model_provider_local.py`, `scripts/prompt.py`, `scripts/tools.py` | Reference implementation of prompt construction, model calls, tool execution, and routing-time decision logic. |



## Dataset Summary

| File | Records | Main fields |
| --- | ---: | --- |
| `datasets/sft_train.json` | 6407 | `query`, `completed_steps`, `thought`, `output`, `instruction`, `available_tools` |
| `datasets/sft_test.json` | 1602 | `query`, `completed_steps`, `thought`, `output`, `instruction`, `available_tools` |
| `datasets/rm_train.jsonl` | 1584 | `input`, `chosen`, `rejected` |
| `datasets/rm_test.jsonl` | 177 | `input`, `chosen`, `rejected` |
| `datasets/ppo_train.jsonl` | 3000 | `input`, `chosen`, `rejected` |
| `datasets/router_classifier_train.jsonl` | 2176 | `query`, `completed_steps`, `local_response`, `label` |
| `datasets/router_classifier_test.jsonl` | 242 | `query`, `completed_steps`, `local_response`, `label` |
| `datasets/frozen_eval.jsonl` | 1000 | `eval_id`, `query`, `completed_steps`, `instruction`, `available_tools`, `reference_action` |
