# InternLM2-zh_CN-Report
InternLM2技术报告翻译  

[**技术报告链接**](https://arxiv.org/pdf/2403.17297.pdf)：https://arxiv.org/pdf/2403.17297.pdf

## 领取方法

在想参与的章节下添加自己的github和link

翻译以excel分栏的格式给出

## 示例如下

| <h3 id="Abstrct">00 Abstrct</h3> |  |
| :------------- | :------------- |
| **English** | **中文翻译** |
|The evolution of Large Language Models (LLMs) like ChatGPT and GPT-4 has sparked discussions on the advent of Artificial General Intelligence (AGI). However, replicating such advancements in open-source models has been challenging. This paper introduces InternLM2, an open-source LLM that outperforms its predecessors in comprehensive evaluations across 6 dimensions and 30 benchmarks, long-context modeling, and open-ended subjective evaluations through innovative pre-training and optimization techniques. The pre-training process of InternLM2 is meticulously detailed, highlighting the preparation of diverse data types including text, code, and long-context data. InternLM2 efficiently captures long-term dependencies, initially trained on 4k tokens before advancing to 32k tokens in pre-training and fine-tuning stages, exhibiting remarkable performance on the 200k “Needle-in-a-Haystack” test. InternLM2 is further aligned using Supervised Fine-Tuning (SFT) and a novel Conditional Online Reinforcement Learning from Human Feedback (COOL RLHF) strategy that addresses conflicting human preferences and reward hacking. By releasing InternLM2 models in different training stages and model sizes, we provide the community with insights into the model’s evolution| **（机翻打样）** ChatGPT 和 GPT-4 等大型语言模型 (LLM) 的发展引发了关于通用人工智能 (AGI) 出现的讨论。然而，在开源模型中复制这些进步一直具有挑战性。本文介绍了 InternLM2，这是一个开源法学硕士，通过创新的预训练和优化技术，它在 6 个维度和 30 个基准的综合评估、长上下文建模和开放式主观评估方面优于其前辈。 InternLM2的预训练过程非常详细，突出了文本、代码、长上下文数据等多种数据类型的准备。 InternLM2 有效地捕获了长期依赖关系，最初在 4k 令牌上进行训练，然后在预训练和微调阶段升级到 32k 令牌，在 200k 的“大海捞针”测试中表现出了出色的性能。 InternLM2 使用监督微调 (SFT) 和新颖的人类反馈条件在线强化学习 (COOL RLHF) 策略进一步协调，该策略可解决人类偏好冲突和奖励黑客问题。通过发布不同训练阶段和模型大小的 InternLM2 模型，我们为社区提供了有关模型演变的见解|
| <h3 id="Introduction">01 Introduction</h3> |  |
| **English** | **中文翻译** |
| context | 中文翻译 |
| 。。。。 | 。。。。 |

## 翻译后的目录

- 00 [Abstrct](#Abstrct)
- 01 [Introduction](#Introduction)
- ...

## 目录
- 0 Abstrct [chg0901](https://github.com/chg0901/)
- 1 Introduction [chg0901](https://github.com/chg0901/)
- 2 Infrastructure 4
  - 2.1 InternEvo . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4
  - 2.2 Model Structure . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 6
- 3 Pre-train 7
  - 3.1 Pre-training data . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 7
    - 3.1.1 Text Data . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 7
    - 3.1.2 Code Data . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 9
    - 3.1.3 Long Context Data . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 11
  - 3.2 Pre-training Settings . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 12
    - 3.2.1 Tokenization . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 13
    - 3.2.2 Pre-training Hyper-parameters . . . . . . . . . . . . . . . . . . . . . . 13
    - 3.3 Pre-training Phases . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 13
    - 3.3.1 4k Context Training . . . . . . . . . . . . . . . . . . . . . . . . . . . . 14
    - 3.3.2 Long Context Training . . . . . . . . . . . . . . . . . . . . . . . . . . . 14
    - 3.3.3 Capability Specific Enhancement Training . . . . . . . . . . . . . . . 14
- 4 Alignment 14
  - 4.1 Supervised Fine-Tuning . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 15
  - 4.2 COOL Reinforcement Learning from Human Feedback . . . . . . . . . . . . 15
    - 4.2.1 Conditional Reward Model . . . . . . . . . . . . . . . . . . . . . . . . 16
    - 4.2.2 Online RLHF . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 17
    - 4.2.3 PPO Training Details . . . . . . . . . . . . . . . . . . . . . . . . . . . . 18
  - 4.3 Long-Context Finetuning . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 20
  - 4.4 Tool-Augmented LLMs . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 20
- 5 Evaluation and Analysis 21
  - 5.1 Overview . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 21
  - 5.2 Performance on Downstream Tasks . . . . . . . . . . . . . . . . . . . . . . . . 21
    - 5.2.1 Comprehensive Examination . . . . . . . . . . . . . . . . . . . . . . . 21
    - 5.2.2 Language and Knowledge . . . . . . . . . . . . . . . . . . . . . . . . . 23
    - 5.2.3 Reasoning and Mathematics . . . . . . . . . . . . . . . . . . . . . . . 24
    - 5.2.4 Coding . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 27
    - 5.2.5 Performance Before and After Enhancement Training . . . . . . . . . 27
    - 5.2.6 Long-context Modeling . . . . . . . . . . . . . . . . . . . . . . . . . . 29
    - 5.2.7 Tool Utilization . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 31
  - 5.3 Performance on Alignment . . . . . . . . . . . . . . . . . . . . . . . . . . . . 31
    - 5.3.1 English Subjective Evaluation . . . . . . . . . . . . . . . . . . . . . . . 33
    - 5.3.2 Chinese Subjective Evaluation . . . . . . . . . . . . . . . . . . . . . . 33
    - 5.3.3 Instruct Following Evaluation . . . . . . . . . . . . . . . . . . . . . . . 34
    - 5.3.4 Ablation Study of Conditional Reward Model . . . . . . . . . . . . . 35
  - 5.4 Discussion on Data Contamination . . . . . . . . . . . . . . . . . . . . . . . . 35
- 6 Conclusion 36
- A Appendix 47
  - A.1 Acknowledgements . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 47
  - A.2 Prompts for Evaluation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 47
