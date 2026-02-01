# BATED: Learning Fair Representation for Pre-Trained Language Models via Biased Teacher-Guided Disentanglement

![rw-book-cover](https://ars.els-cdn.com/content/image/1-s2.0-S0004370225X00072-cov150h.gif)

## Metadata
- Author: [[ScienceDirect Publication: Artificial Intelligence]]
- Full Title: BATED: Learning Fair Representation for Pre-Trained Language Models via Biased Teacher-Guided Disentanglement
- Category: #articles
- Document Note: 1. How does the biased teacher-guided disentanglement approach in BATED effectively separate fair and biased representations without relying on sensitive attribute information?
   2. In what ways does causal contrastive learning contribute to training a task-agnostic biased teacher model, and how does this impact the debiasing performance across different downstream tasks?
   3. How does BATED balance improving fairness in PLMs' downstream task decisions while maintaining or enhancing overall model performance compared to existing intrinsic and extrinsic debiasing methods?
- Summary: This paper introduces BATED, a method to reduce social bias in pre-trained language models using a biased teacher model to guide fair representation learning. BATED separates biased and fair information in the model's encoding without needing sensitive attribute data, protecting privacy. Experiments show BATED improves fairness and keeps strong performance on multiple language tasks.
- URL: https://www.sciencedirect.com/science/article/pii/S0004370225001201?dgcid=rss_sd_all

## Full Document
#### Abstract

With the rapid development of Pre-trained Language Models (PLMs) and their widespread deployment in various real-world applications, social biases of PLMs has attracted increasing attention, especially the fairness of downstream tasks, which potentially affects the development and stability of society. Among existing debiasing methods, intrinsic debiasing methods are not necessarily effective when applied to downstream tasks, and the downstream fine-tuning process may introduce new biases or catastrophic forgetting. Most extrinsic debiasing methods rely on sensitive attribute words as prior knowledge to supervise debiasing training. However, it is difficult to collect sensitive attribute information of real data due to privacy and regulation. Moreover, limited sensitive attribute words may lead to inadequate debiasing training. To this end, this paper proposes a debiasing method to learn fair representation for PLMs via **B**i**A**sed **TE**acher-guided **D**isentanglement (called **BATED**). Specific to downstream tasks, BATED performs debiasing training under the guidance of a biased teacher model rather than relying on sensitive attribute information of the training data. First, we leverage causal contrastive learning to train a task-agnostic general biased teacher model. We then employ Variational Auto-Encoder (VAE) to disentangle the PLM-encoded representation into the fair representation and the biased representation. The Biased representation is further decoupled via biased teacher-guided disentanglement, while the fair representation learn downstream tasks. Therefore, BATED guarantees the performance of downstream tasks while improving the fairness. Experimental results on seven PLMs testing three downstream tasks demonstrate that BATED outperforms the state-of-the-art overall in terms of fairness and performance on downstream tasks.

#### Introduction

Pre-trained Language Models (PLMs), such as BERT [1], GPT-2 [2], and Large Language Models (LLMs) like LLaMA-3 [3], [4] and GPT-4 [5], have been widely adopted across various Natural Language Processing (NLP) tasks due to their powerful language modeling capabilities. However, PLMs have been shown to suffer from social biases that carry over from the representation into decisions on downstream tasks [6], [7], and may even compromise real-world NLP systems. For example, the automatic resume filtering system [8], [9] may have the gender bias, which is more inclined to assign “*male*” applicants to “*doctors*” and “*female*” applicants to “*nurses*” for the same resumes. The US healthcare system [10], [11] is found to be racially biased in that for “*white*” patients and “*black*” patients with the same level of risk, it calculates a higher prevalence for “*black*” patients. The application of PLMs with social biases will further aggravate the adverse social situation of vulnerable groups who are discriminated against and marginalized, with potential social harm and unpredictable impact. Therefore, a growing number of researchers have focused on mitigating the social biases of PLMs to improve the fairness of decisions in downstream tasks.

The social biases of PLMs can be roughly divided into two main categories: intrinsic bias and extrinsic bias [12]. Intrinsic bias, also known as upstream bias or representation bias, refers to harmfulness in the representation encoded by PLMs. Extrinsic bias, also known as downstream bias or decision bias, quantifies the fairness of PLMs predictions on downstream tasks. In recent years, there are proposed many debiasing methods to mitigate the social biases of PLMs. Corresponding to the type of biases, debiasing methods can be divided into intrinsic debiasing methods and extrinsic debiasing methods [12]. Intrinsic debiasing methods are task-agnostic and performed before downstream tasks, aiming to improve fairness of PLM-encoded representations. Extrinsic debiasing methods are task-specific and performed during fine-tuning of downstream tasks, aiming to improve the fairness of decisions made by PLMs.

Intrinsic debiasing methods mitigate the intrinsic bias by debiasing the representation of the PLMs' encoder output. A representative approach is Counterfactual Data Augmentation (CDA) [13], [14], which uses sensitive attribute words pairs (e.g., “*male*” and “*female*” specific to gender groups, “*white*” and “*black*” specific to race groups) to match and replace the original samples and then retrain PLMs with augmented sample pairs. FairFil [15], MABEL [16], and CCPA [17] combine CDA and contrastive learning [18] to debias by approximating the representation between augmented sample pairs. In addition, methods such as Auto-Debias [19] searching for biased prompts, BNS [20] masking biased neurons, and DeepSoftDebias [21] utilizing residual neural networks all target intrinsic bias. Although intrinsic debiasing methods are universal because they do not restrict downstream tasks, there are some drawbacks when applied to downstream tasks. On the one hand, it is not certain that there is a necessary relationship between intrinsic and extrinsic bias [22], [23]. On the other hand, fine-tuning on downstream tasks may induce catastrophic forgetting [24] or introduce additional new biases [25]. Therefore, the debiasing performance of PLMs trained with intrinsic debiasing methods will be weakened in downstream tasks.

Extrinsic debiasing designs mitigation strategies for specific downstream tasks, which are usually based on adversarial training [26], [27], orthogonal projection [28], and regularization constraints [29]. Most of them take sensitive attribute words as prior knowledge to supervise the debiasing training. However, due to the limitations of privacy and regulation, it may be difficult to collect sensitive attribute information of real data. In addition, the hand-crafted sensitive attribute words are limited and difficult to cover all the training data, resulting in inadequate debiasing training.

Motivated by the above challenges, this paper proposes a debiasing method to learn fair representation for PLMs via **B**i**A**sed **TE**acher-guided **D**isentanglement (called **BATED**). Specific to downstream tasks, BATED performs debiasing training under the guidance of a biased teacher model rather than relying on sensitive attribute information of the training data. Specifically, we first train a task-agnostic general biased teacher model using causal contrastive learning [30]. In the debiasing training phase, we use a Variational Auto-Encoder (VAE) [31], [32] to disentangle the PLM-encoded representation into a fair representation and a biased representation. The biased teacher model is then used to encourage the distillation of the biased representation. Downstream task loss is used to constrain the fair representation to learn task-related information. Extensive experiments show that BATED improves decision fairness while maintaining the performance of PLMs in downstream tasks. Our contributions are summarized as follows.

* We propose a debiasing method that uses a biased teacher model to guide the VAE for feature disentanglement. It can mitigate the social biases of PLMs in the debiasing training process without relying on the sensitive attribute information of the data, which makes the debiasing method not limited by data privacy and expands the scope of application.
* We propose a method to train a task-agnostic general biased teacher model using causal contrastive learning, and design a feature distillation loss that utilizes a biased teacher model to guide biased feature disentanglement.
* Extensive debiasing experiments are conducted on seven PLMs: BERT, DistilBERT, ELECTRA, OPT, GPT-2, Qwen-2.5, and LLaMA-3.2 on three downstream tasks. The experimental results demonstrate that our proposed debiasing method BATED generally outperforms the state-of-the-art overall in terms of fairness and performance on downstream tasks.

#### Section snippets

#### Related Work

In research related to PLMs, the concept of bias spans multiple domains, such as model bias under out-of-distribution (OOD) generalization scenarios [33] and other forms of inductive or task-specific biases. In this paper, we focus specifically on social biases related to model fairness, which concern the equitable treatment of different demographic or identity groups in the predictions of PLMs. In this section, we introduce recent debiasing methods to mitigate the social biases of PLMs from

#### Preliminaries

Specific to demographic groups, a *social sensitive topic*

T={T1,T2,⋯,TN} contains *N* bias directions, each of which corresponds to a *social subgroup*, and each social subgroup can be represented by a set of *sensitive attribute words*

(t1,t2,⋯,tm). In this paper, we consider the binary gender group

Gender={Male,Famale},1

#### Methodology

In this section, we propose the debiasing method BATED to learn the fair representation for PLMs in downstream tasks via biased teacher-guided disentanglement. BATED consists of two stages: 1) training the biased teacher model; and 2) debiasing training via biased teacher-guided disentanglement. The framework of BATED is shown in Figure 1. In the first stage, we propose to exploit causal contrastive learning to train the PLM's encoder as a biased teacher model, amplifying the intrinsic gender

#### Experiments

In this section, in order to verify the effectiveness of our proposed debiasing method, we conduct a comprehensive experimental analysis of BATED by answering the following four Research Questions (RQ).

**RQ1**: How effective is applying BATED to debias PLMs in downstream tasks?

**RQ2**: How effective is the training strategy for causal contrastive learning?

**RQ3**: How each module in BATED contributes to the performance of the model?

**RQ4**: How well does BATED generalize for debiasing out-of-domain tasks?

#### Conclusions and Future Work

In this paper, we propose a debiasing method to mitigate the social biases of PLMs in downstream tasks, which learns fair representation via the biased teacher-guided disentanglement. We employ VAE to disenttangle PLM-encoded representation into the fair representation and the biased representation, and leverage the biased teacher model to guide further decoupling of biased representation, while the fair representation is constrained by task loss. Furthermore, we design strategies that leverage

#### CRediT authorship contribution statement

**Yingji Li:** Writing – original draft, Methodology, Formal analysis, Conceptualization, Validation, Investigation, Data curation. **Mengnan Du:** Supervision, Methodology. **Rui Song:** Methodology, Formal analysis. **Mu Liu:** Formal analysis, Validation, Writing – review & editing, Investigation, Visualization. **Ying Wang:** Project administration, Supervision, Funding acquisition.

#### Acknowledgements

We express gratitude to the anonymous reviewers for their hard work and kind comments. The work was supported in part by the National Natural Science Foundation of China (No. 62272191), the International Science and Technology Cooperation Program of Jilin Province (No. 20230402076GH, No. 20240402067GH), the Science and Technology Development Program of Jilin Province (No. 20220201153GX), the China Postdoctoral Science Foundation Funded Project (No. 2024M761122).

#### References (78)

* J. Devlin, M. Chang, K. Lee, K. Toutanova, BERT: pre-training of deep bidirectional transformers for language...
* A. Radford, J. Wu, R. Child, D. Luan, D. Amodei, I. Sutskever, et al., Language models are unsupervised multitask...
* T. B. Brown, B. Mann, N. Ryder, M. Subbiah, J. Kaplan, P. Dhariwal, A. Neelakantan, P. Shyam, G. Sastry, A. Askell, S....
* AI@Meta, Llama 3 model card. URL...
* OpenAI, GPT-4 technical report, CoRR abs/2303.08774. arXiv:2303.08774, doi:10.48550/ARXIV.2303.08774. URL...
* A. Caliskan, J. J. Bryson, A. Narayanan, Semantics derived automatically from language corpora contain human-like...
* P. Chen, X. Guo, Y. Li, X. Zhang, Z. Feng, Mitigating language bias of lmms in social intelligence understanding with...
* K. V. Deshpande, S. Pan, J. R. Foulds, Mitigating demographic bias in ai-based resume filtering, in: Proc. 28th UMAP...
* L. Ding, Y. Hu, N. Denier, E. Shi, J. Zhang, Q. Hu, K. D. Hughes, L. Kong, B. Jiang, Probing social bias in labor...
* Z. Obermeyer, B. Powers, C. Vogeli, S. Mullainathan, Dissecting racial bias in an algorithm used to manage the health...

- M. Moukheiber, L. Moukheiber, D. Moukheiber, H. Lee, Unmasking societal biases in respiratory support for ICU patients...

- Y. Li, M. Du, R. Song, X. Wang, Y. Wang, A survey on fairness in large language models, CoRR abs/2308.10149....

- K. Webster, X. Wang, I. Tenney, A. Beutel, E. Pitler, E. Pavlick, J. Chen, S. Petrov, Measuring and reducing gendered...

- K. Lu, P. Mardziel, F. Wu, P. Amancharla, A. Datta, Gender bias in neural natural language processing, in: Proceedings...

- P. Cheng, W. Hao, S. Yuan, S. Si, L. Carin, Fairfil: Contrastive neural debiasing method for pretrained text encoders,...

- J. He, M. Xia, C. Fellbaum, D. Chen, MABEL: attenuating gender bias using textual entailment data, in: Proceedings of...

- Y. Li, M. Du, X. Wang, Y. Wang, Prompt tuning pushes farther, contrastive learning pulls closer: A two-stage approach...

- Z. Yang, Y. Cheng, Y. Liu, M. Sun, Reducing word omission errors in neural machine translation: A contrastive learning...

- Y. Guo, Y. Yang, A. Abbasi, Auto-debias: Debiasing masked language models with automated biased prompts, in: Proc. 60th...

- Y. Liu, Y. Liu, X. Chen, P. Chen, D. Zan, M. Kan, T. Ho, The devil is in the neurons: Interpreting and mitigating...

- A. Rakshit, S. Singh, S. Keshari, A. G. Chowdhury, V. Jain, A. Chadha, From prejudice to parity: A new approach to...

- S. Goldfarb-Tarrant, R. Marchant, R. M. Sánchez, M. Pandya, A. Lopez, Intrinsic bias metrics do not correlate with...

- T. Katô, Y. Miyao, Analyzing correlations between intrinsic and extrinsic bias metrics of static word embeddings with...

- Z. Fatemi, C. Xing, W. Liu, C. Xiong, Improving gender fairness of pre-trained language models without catastrophic...

- R. B. Loureiro, T. P. Pagano, F. V. N. Lisboa, L. F. S. Nascimento, E. L. S. de Oliveira, I. Winkler, E. G. S....

- X. Han, T. Baldwin, T. Cohn, Decoupling adversarial training for fair NLP, in: C. Zong, F. Xia, W. Li, R. Navigli...

- S. Ravfogel, M. Twiton, Y. Goldberg, R. D. Cotterell, Linear adversarial concept erasure, in: Proceedings of the 39th...

- S. Ravfogel, Y. Elazar, H. Gonen, M. Twiton, Y. Goldberg, Null it out: Guarding protected attributes by iterative...

- S. Ghanbarzadeh, Y. Huang, H. Palangi, R. C. Moreno, H. Khanpour, Gender-tuning: Empowering fine-tuning for debiasing...

- S. Choi, M. Jeong, H. Han, S. Hwang, C2L: causally contrastive learning for robust text classification, in:...

- D. P. Kingma, M. Welling, Auto-encoding variational bayes, in: 2nd International Conference on Learning...

- Y. Bao, H. Zhou, S. Huang, L. Li, L. Mou, O. Vechtomova, X. Dai, J. Chen, Generating sentences from disentangled...

- A. Liusie, Y. Fathullah, M. J. F. Gales, Teacher-student training for debiasing: General permutation debiasing for...

- P. P. Liang, I. M. Li, E. Zheng, Y. C. Lim, R. Salakhutdinov, L. Morency, Towards debiasing sentence representations,...

- R. Zmigrod, S. J. Mielke, H. M. Wallach, R. Cotterell, Counterfactual data augmentation for mitigating gender...

- M. L. Olson, R. Khanna, L. Neal, F. Li, W. Wong, Counterfactual state explanations for reinforcement learning agents...

- Y. Li, M. Du, R. Song, X. Wang, M. Sun, Y. Wang, Mitigating social biases of pre-trained language models via...

- M. Standen, J. Kim, C. Szabo, Adversarial machine learning attacks and defences in multi-agent reinforcement learning,...

- N. Torres, Contrastive adversarial gender debiasing, Nat. Lang. Process. J. 8 (2024) 100092....
