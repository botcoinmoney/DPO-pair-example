An example of the current working version (subject to change) of DPO training pairs produced by the BOTCOIN mining system. 
 
## Dataset / record fields

Each file is a fully self-contained HF training row containing:


| Field | Content |
|-------|---------|
| `document` | Full ~22K char numbered prose document (what the miner saw) |
| `questions` | All 10 questions |
| `constraints` | All 9 constraint descriptions |
| `trap_metadata` | Trap details (entity, attribute, wrong/correct values) |
| `prompt` | Ready-to-use model input (document + questions + constraints) |
| `rejected` / `rejected_text` | Failed attempt: structured + flattened trace + artifact |
| `chosen` / `chosen_text` | Passing attempt: structured + flattened trace + artifact |
| `rejected_metadata` / `chosen_metadata` | Full per-attempt annotations (constraints, trace stats, spatial summary, timing) |
| `pair_annotations` | Constraint flips, revision time, trace shape deltas, feedback shown between attempts |


## What is DPO?

From HuggingFace:

"TRL supports the Direct Preference Optimization (DPO) Trainer for training language models, as described in the paper Direct Preference Optimization: Your Language Model is Secretly a Reward Model by Rafael Rafailov, Archit Sharma, Eric Mitchell, Stefano Ermon, Christopher D. Manning, Chelsea Finn.

The abstract from the paper is the following:

While large-scale unsupervised language models (LMs) learn broad world knowledge and some reasoning skills, achieving precise control of their behavior is difficult due to the completely unsupervised nature of their training. Existing methods for gaining such steerability collect human labels of the relative quality of model generations and fine-tune the unsupervised LM to align with these preferences, often with reinforcement learning from human feedback (RLHF). However, RLHF is a complex and often unstable procedure, first fitting a reward model that reflects the human preferences, and then fine-tuning the large unsupervised LM using reinforcement learning to maximize this estimated reward without drifting too far from the original model. In this paper we introduce a new parameterization of the reward model in RLHF that enables extraction of the corresponding optimal policy in closed form, allowing us to solve the standard RLHF problem with only a simple classification loss. The resulting algorithm, which we call Direct Preference Optimization (DPO), is stable, performant, and computationally lightweight, eliminating the need for sampling from the LM during fine-tuning or performing significant hyperparameter tuning. Our experiments show that DPO can fine-tune LMs to align with human preferences as well as or better than existing methods. Notably, fine-tuning with DPO exceeds PPO-based RLHF in ability to control sentiment of generations, and matches or improves response quality in summarization and single-turn dialogue while being substantially simpler to implement and train.

This post-training method was contributed by Kashif Rasul and later refactored by Quentin Gallouédec."
