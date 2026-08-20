# Sourav Verma’s Post

![rw-book-cover](https://static.licdn.com/aero-v1/sc/h/c45fy346jw096z9pbphyyhdz7)

## Metadata
- Author: [[Sourav Verma]]
- Full Title: Sourav Verma’s Post
- Category: #articles
- Document Tags: [[ai]] [[inbox]] 
- Summary: Decreasing numerical precision in models often keeps intelligence intact because most weights are near zero and only a few need high precision. Using techniques like outlier-aware quantization reduces memory use and speeds up processing by focusing precision where it matters most. This helps fit large models on smaller hardware while maintaining accuracy, as intelligence depends on structure, not exact numbers.
- URL: https://www.linkedin.com/posts/srgrace_ai-llms-finetuning-activity-7414674699881820161-1XkZ?utm_source=share&utm_medium=member_ios&rcm=ACoAADaPBDUBURpz_gIBHBp-B7d7MQl-YeSyFGw

## Full Document
[Sourav Verma](https://in.linkedin.com/in/srgrace?trk=public_post_feed-actor-name) 

You're in an NVIDIA Deep Learning Performance Engineer interview.

The question:  

"We are moving from FP16 to INT8, INT4, and even 1.58-bit (Binary) models. Why does decreasing numerical precision often result in almost zero loss in 'intelligence'?"

You pause - most jump to "Models are over-parameterized."

You reply:  

 - LLM weights aren't uniformly distributed; they follow a heavy-tailed distribution. Most weights are near zero and contribute little to the final output.  

 - High precision (FP32/16) is necessary during training to capture tiny gradient updates. But during inference, the features the model has learned are robust enough that close enough is often perfect.  

 - We use 'Outlier-aware Quantization.' We find the 0.1% of feature weights that have huge magnitudes and keep them in high precision, while squashing the rest into 4 bits.

The interviewer probes:  

"What is the actual physical bottleneck we are solving here?"

You explain:  

 - It's the 'Memory Wall.' - Moving a 16-bit number from VRAM to the CUDA core consumes orders of magnitude more energy and time than the actual multiplication.  

 - By moving to 4-bit, we quadruple the effective memory bandwidth. We can fit a 70B parameter model on a single consumer GPU that would otherwise require an enterprise cluster.  

 - We also utilize 'Weight-Only Quantization' where we dequantize back to FP16 just for the calculation, saving memory space while maintaining math accuracy.

Finally, you add:  

"Intelligence is about the topology of the high-dimensional space, not the precision of the coordinates. Quantization is just finding a more efficient way to map that."

[#AI](https://www.linkedin.com/signup/cold-join?session_redirect=https%3A%2F%2Fwww.linkedin.com%2Ffeed%2Fhashtag%2Fai&trk=public_post-text) [#LLMs](https://www.linkedin.com/signup/cold-join?session_redirect=https%3A%2F%2Fwww.linkedin.com%2Ffeed%2Fhashtag%2Fllms&trk=public_post-text) [#FineTuning](https://www.linkedin.com/signup/cold-join?session_redirect=https%3A%2F%2Fwww.linkedin.com%2Ffeed%2Fhashtag%2Ffinetuning&trk=public_post-text)
