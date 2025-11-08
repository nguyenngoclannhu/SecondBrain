# Manoranjan Rajguru’s Post

![rw-book-cover](https://static.licdn.com/aero-v1/sc/h/c45fy346jw096z9pbphyyhdz7)

## Metadata
- Author: [[Manoranjan Rajguru]]
- Full Title: Manoranjan Rajguru’s Post
- Category: #articles
- Document Tags: [[ai]] 
- Summary: LoRA can match full fine-tuning but only if used correctly: apply it to all layers (especially MLPs), choose enough rank to cover dataset information, use proper LR (≈10× full-FT), moderate batch sizes, and train long enough.  
LoRA fails when used attention-only, with too-small capacity, very large batches, wrong LR, or short training.  
In interviews, justify choice by weighing capacity, layer placement, batch size, learning rate, and training duration.
- URL: https://www.linkedin.com/posts/manoranjan-rajguru_machinelearning-llm-finetuning-share-7379033079321034752-TioQ?utm_source=share&utm_medium=member_ios&rcm=ACoAADaPBDUBURpz_gIBHBp-B7d7MQl-YeSyFGw

## Full Document
[Manoranjan Rajguru](https://in.linkedin.com/in/manoranjan-rajguru?trk=public_post_feed-actor-name) 

Generative AI at Microsoft ex Amazon

You're in a ML Engineer interview at Microsoft, and the interviewer asks:  

"We're building fine-tuning infrastructure for 100+ customer models. Should we use LoRA or full fine-tuning? Justify your choice."

Here's how you can answer:  

A. Most candidates fumble here because they only know "LoRA saves memory." Incomplete answer.  

B. There are 5 critical factors every ML engineer should understand cold.

1. The Capacity Question - The make-or-break decision  

LoRA works by decomposing weight updates: W' = W + γBA  

Where B and A are low-rank matrices with FAR fewer parameters than W.  

The brutal truth? LoRA underperforms when your dataset exceeds its capacity.  

Rule of thumb: Neural networks store ~2 bits per parameter. Your 50K instruction dataset with 1 bit/token loss? You need enough LoRA parameters to absorb that information.

2. Which Layers Get LoRA? - Where 90% of engineers go wrong  

Most people apply LoRA ONLY to attention layers (following the original paper).  

Wrong move.  

Recent experiments show attention-only LoRA underperforms even when you match parameter counts with higher rank.  

The winner: Apply LoRA to ALL layers, especially MLP/MoE layers where most parameters live.  

Example on Llama-3.1-8B:  

MLP-only (rank 128): 0.24B params ✅  

Attention-only (rank 256): 0.25B params ❌  

Same parameter count. MLP-only wins. Why? Because training dynamics depend on where parameters are, not just how many.

3. The Batch Size Penalty - The hidden performance killer  

Here's what separates junior from senior ML engineers:  

LoRA degrades FASTER than full fine-tuning as batch size increases.  

And it's independent of rank.  

Rank-1, rank-256, rank-512... all show the same degradation pattern at large batches.

4. The Learning Rate Mystery - 10x faster, but why?  

Optimal LoRA learning rate is consistently 10x higher than full fine-tuning.  

Across ALL model sizes. 8B to 70B parameters. Llama, Qwen, doesn't matter.  

Empirical fact: LoRA LR = 10 × FullFT LR  

The kicker? We don't have a complete theoretical explanation for this 10x ratio.  

The 1/r scaling factor makes optimal LR approximately rank-invariant (rank-1 and rank-512 use similar LRs). But the 10x boost over FullFT? Still an open question.

When LoRA matches full fine-tuning:   

✅ Applied to all layers (especially MLPs)   

✅ Rank × 2 bits/param > dataset information content   

✅ Reasonable batch sizes (<512)   

✅ LR properly tuned (10× FullFT optimal)   

✅ Training long enough (B matrix grows to match A scale)

When LoRA underperforms:   

❌ Attention-only   

❌ Dataset too large for capacity   

❌ Very large batches (1024+)   

❌ Wrong LR (using FullFT learning rate)   

❌ Short training with low LR

[#MachineLearning](https://www.linkedin.com/signup/cold-join?session_redirect=https%3A%2F%2Fwww.linkedin.com%2Ffeed%2Fhashtag%2Fmachinelearning&trk=public_post-text) [#LLM](https://www.linkedin.com/signup/cold-join?session_redirect=https%3A%2F%2Fwww.linkedin.com%2Ffeed%2Fhashtag%2Fllm&trk=public_post-text) [#FineTuning](https://www.linkedin.com/signup/cold-join?session_redirect=https%3A%2F%2Fwww.linkedin.com%2Ffeed%2Fhashtag%2Ffinetuning&trk=public_post-text) [#MLOps](https://www.linkedin.com/signup/cold-join?session_redirect=https%3A%2F%2Fwww.linkedin.com%2Ffeed%2Fhashtag%2Fmlops&trk=public_post-text) [#AI](https://www.linkedin.com/signup/cold-join?session_redirect=https%3A%2F%2Fwww.linkedin.com%2Ffeed%2Fhashtag%2Fai&trk=public_post-text) [#DeepLearning](https://www.linkedin.com/signup/cold-join?session_redirect=https%3A%2F%2Fwww.linkedin.com%2Ffeed%2Fhashtag%2Fdeeplearning&trk=public_post-text) [#LoRA](https://www.linkedin.com/signup/cold-join?session_redirect=https%3A%2F%2Fwww.linkedin.com%2Ffeed%2Fhashtag%2Flora&trk=public_post-text) [#Microsoft](https://www.linkedin.com/signup/cold-join?session_redirect=https%3A%2F%2Fwww.linkedin.com%2Ffeed%2Fhashtag%2Fmicrosoft&trk=public_post-text) [#Interview](https://www.linkedin.com/signup/cold-join?session_redirect=https%3A%2F%2Fwww.linkedin.com%2Ffeed%2Fhashtag%2Finterview&trk=public_post-text) [#NaturalLanguageProcessing](https://www.linkedin.com/signup/cold-join?session_redirect=https%3A%2F%2Fwww.linkedin.com%2Ffeed%2Fhashtag%2Fnaturallanguageprocessing&trk=public_post-text) [#ProductionML](https://www.linkedin.com/signup/cold-join?session_redirect=https%3A%2F%2Fwww.linkedin.com%2Ffeed%2Fhashtag%2Fproductionml&trk=public_post-text)
