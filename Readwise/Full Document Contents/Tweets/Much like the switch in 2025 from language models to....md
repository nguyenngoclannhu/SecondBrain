# Much like the switch in 2025 from language models to...

![rw-book-cover](https://pbs.twimg.com/profile_images/1985433557448216576/qwc8NvJ9.jpg)

## Metadata
- Author: [[Alex L Zhang]]
- Full Title: Much like the switch in 2025 from language models to...
- Category: #tweets
- Summary: Researchers propose Recursive Language Models (RLMs) as a new way to scale beyond current LLM context limits. RLMs let the model treat its prompt as data, write code, and call LLMs recursively to process very long inputs. Experiments show RLMs keep strong performance on tasks up to 1M tokens and beat other methods at similar cost.
- URL: https://x.com/a1zhang/status/2007198916073136152/?utm_medium=email&rw_tt_thread=True

## Full Document
Much like the switch in 2025 from language models to reasoning models, we think 2026 will be all about the switch to Recursive Language Models (RLMs).

It turns out that models can be far more powerful if you allow them to treat \*their own prompts\* as an object in an external environment, which they understand and manipulate by writing code that invokes LLMs!

Our full paper on RLMs is now available—with much more expansive experiments compared to our initial blogpost from October 2025!

<https://t.co/x47pIfIkTb>

![](https://pbs.twimg.com/media/G9r_9C3XYAA7Psq.jpg)

---

RLMs are our bitter-lesson-pilled approach to inference-time scaling, and they can scale the context size of LLMs by orders of magnitude!

From the outside, an RLM exposes the same interface as a language model. It accepts a string prompt and produces a string response. But, internally, RLMs do not feed the prompt directly to the Transformer.

Instead, they set up the LLM in a REPL environment where the prompt \*is placed into a variable\*, and then allow the LLM to write code to peek into, break up, and recursively invoke itself over snippets of the prompt.

![](https://pbs.twimg.com/media/G9sAGzYXUAA4O_v.jpg)

---

We experiment on several different tasks of varying levels of complexity, with one closed and one open LLM.

We apply well-known task agnostic baselines, including context compaction (summarization), CodeAct with a retriever, and of course the base LLM itself.

Across all tasks and a closed and open frontier model, RLMs outperform other methods at a cheaper or comparable cost.

![](https://pbs.twimg.com/media/G9sAWsYWsAA_qHE.jpg)

---

We hypothesize that model performance degrades on long context tasks at different rates depending on the complexity of the task.

We scale GPT-5 and RLM(GPT-5) performance at input context lengths from 8K to 1M tokens on 3 tasks of increasing difficulty and show that the base model performance degrades pretty dramatically, while RLMs maintain strong performance and can handle contexts well beyond the window of the base model.

![](https://pbs.twimg.com/media/G9sAcC-WQAAn9FI.jpg)

---

We are excited by all the current interest and future work on RLMs, including the recent blogpost by [@PrimeIntellect](https://twitter.com/PrimeIntellect) and [@omouamoua](https://twitter.com/omouamoua).

This work would not be possible without support from the [@LaudeInstitute](https://twitter.com/LaudeInstitute), and help from labmates [@NoahZiems](https://twitter.com/NoahZiems) [@jacobli99](https://twitter.com/jacobli99) and [@nlp\_mit](https://twitter.com/nlp_mit)!

Paper Link: <https://t.co/x47pIfIkTb>
