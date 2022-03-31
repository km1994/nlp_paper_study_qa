# 【关于 NLP】 那些你不知道的事 —— 问答系统篇

> 作者：杨夕
> 
> 介绍：研读顶会论文，复现论文相关代码
> 
> NLP 百面百搭 地址：https://github.com/km1994/NLP-Interview-Notes
> 
> **[手机版NLP百面百搭](https://mp.weixin.qq.com/s?__biz=MzAxMTU5Njg4NQ==&mid=100005719&idx=3&sn=5d8e62993e5ecd4582703684c0d12e44&chksm=1bbff26d2cc87b7bf2504a8a4cafc60919d722b6e9acbcee81a626924d80f53a49301df9bd97&scene=18#wechat_redirect)**
> 
> 推荐系统 百面百搭 地址：https://github.com/km1994/RES-Interview-Notes
> 
> **[手机版推荐系统百面百搭](https://mp.weixin.qq.com/s/b_KBT6rUw09cLGRHV_EUtw)**
> 
> 搜索引擎 百面百搭 地址：https://github.com/km1994/search-engine-Interview-Notes 【编写ing】
> 
> NLP论文学习笔记：https://github.com/km1994/nlp_paper_study
> 
> 推荐系统论文学习笔记：https://github.com/km1994/RS_paper_study
> 
> GCN 论文学习笔记：https://github.com/km1994/GCN_study
> 
> **推广搜 军火库**：https://github.com/km1994/recommendation_advertisement_search
![](other_study/resource/pic/微信截图_20210301212242.png)

> 手机版笔记，可以关注公众号 **【关于NLP那些你不知道的事】** 获取，并加入 【NLP && 推荐学习群】一起学习！！！

> 注：github 网页版 看起来不舒服，可以看 **[手机版NLP论文学习笔记](https://mp.weixin.qq.com/s?__biz=MzAxMTU5Njg4NQ==&mid=100005719&idx=1&sn=14d34d70a7e7cbf9700f804cca5be2d0&chksm=1bbff26d2cc87b7b9d2ed12c8d280cd737e270cd82c8850f7ca2ee44ec8883873ff5e9904e7e&scene=18#wechat_redirect)**

- [【关于 NLP】 那些你不知道的事](#关于-nlp-那些你不知道的事)
  - [介绍](#介绍)
    - [【关于 论文工具】那些你不知道的事](#关于-论文工具那些你不知道的事)
    - [NLP 学习篇](#nlp-学习篇)
      - [经典会议论文研读篇](#经典会议论文研读篇)
      - [理论学习篇](#理论学习篇)
        - [经典论文研读篇](#经典论文研读篇)
        - [【关于 transformer 】 那些的你不知道的事](#关于-transformer--那些的你不知道的事)
        - [【关于 预训练模型】 那些的你不知道的事](#关于-预训练模型-那些的你不知道的事)
        - [【关于 Prompt】 那些的你不知道的事](#关于-prompt-那些的你不知道的事)
          - [【关于 Prompt For NER】 那些的你不知道的事](#关于-prompt-for-ner-那些的你不知道的事)
        - [【关于 信息抽取】 那些的你不知道的事](#关于-信息抽取-那些的你不知道的事)
          - [【关于 实体关系联合抽取】 那些的你不知道的事](#关于-实体关系联合抽取-那些的你不知道的事)
          - [【关于 命名实体识别】那些你不知道的事](#关于-命名实体识别那些你不知道的事)
          - [【关于 关系抽取】那些你不知道的事](#关于-关系抽取那些你不知道的事)
          - [【关于 文档级别关系抽取】那些你不知道的事](#关于-文档级别关系抽取那些你不知道的事)
          - [【关于 事件抽取】那些你不知道的事](#关于-事件抽取那些你不知道的事)
          - [【关于 关键词提取】 那些你不知道的事](#关于-关键词提取-那些你不知道的事)
          - [【关于 新词发现】 那些你不知道的事](#关于-新词发现-那些你不知道的事)
        - [【关于 知识图谱 】 那些的你不知道的事](#关于-知识图谱--那些的你不知道的事)
          - [【关于 实体链指篇】 那些的你不知道的事](#关于-实体链指篇-那些的你不知道的事)
          - [【关于 实体消歧 】 那些的你不知道的事](#关于-实体消歧--那些的你不知道的事)
          - [【关于KGQA 】 那些的你不知道的事](#关于kgqa--那些的你不知道的事)
          - [【关于Neo4j  】 那些的你不知道的事](#关于neo4j---那些的你不知道的事)
        - [【关于 NLP Trick】 那些你不知道的事](#关于-nlp-trick-那些你不知道的事)
          - [【关于 Dropout】 那些你不知道的事](#关于-dropout-那些你不知道的事)
          - [【关于 主动学习】 那些的你不知道的事](#关于-主动学习-那些的你不知道的事)
          - [【关于 对抗训练】 那些的你不知道的事](#关于-对抗训练-那些的你不知道的事)
          - [【关于 文本预处理】 那些的你不知道的事](#关于-文本预处理-那些的你不知道的事)
          - [【关于 半监督学习】 那些的你不知道的事](#关于-半监督学习-那些的你不知道的事)
          - [【关于 GCN in NLP 】那些你不知道的事](#关于-gcn-in-nlp-那些你不知道的事)
        - [【关于 问答系统】 那些的你不知道的事](#关于-问答系统-那些的你不知道的事)
          - [【关于 FAQ 】那些你不知道的事](#关于-faq-那些你不知道的事)
          - [【关于 多轮检索 】那些你不知道的事](#关于-多轮检索-那些你不知道的事)
          - [【关于 KBFAQ 】那些你不知道的事](#关于-kbfaq-那些你不知道的事)
        - [【关于 对话系统】 那些的你不知道的事](#关于-对话系统-那些的你不知道的事)
          - [【关于 自然语言理解 NLU】那些你不知道的事](#关于-自然语言理解-nlu那些你不知道的事)
          - [【关于 状态追踪（DST）】那些你不知道的事](#关于-状态追踪dst那些你不知道的事)
          - [【关于 自然语言生成NLG 】那些你不知道的事](#关于-自然语言生成nlg-那些你不知道的事)
          - [【关于 E2E 】那些你不知道的事](#关于-e2e-那些你不知道的事)
          - [【关于 Rasa 】 那些的你不知道的事](#关于-rasa--那些的你不知道的事)
        - [【关于 文本摘要】 那些的你不知道的事](#关于-文本摘要-那些的你不知道的事)
        - [【关于 文本匹配】 那些的你不知道的事](#关于-文本匹配-那些的你不知道的事)
        - [【关于 机器翻译】 那些的你不知道的事](#关于-机器翻译-那些的你不知道的事)
        - [【关于 文本生成】 那些的你不知道的事](#关于-文本生成-那些的你不知道的事)
        - [【关于 NLP分类任务】那些你不知道的事](#关于-nlp分类任务那些你不知道的事)
          - [【关于 细粒度情感分析】 那些的你不知道的事](#关于-细粒度情感分析-那些的你不知道的事)
        - [【关于 中文分词】那些你不知道的事](#关于-中文分词那些你不知道的事)
        - [【关于 搜索引擎】 那些你不知道的事](#关于-搜索引擎-那些你不知道的事)
        - [【关于 文本纠错】 那些你不知道的事](#关于-文本纠错-那些你不知道的事)
        - [【关于 Text-to-SQL】 那些你不知道的事](#关于-text-to-sql-那些你不知道的事)
      - [实战篇](#实战篇)
        - [重点推荐篇](#重点推荐篇)
    - [会议收集篇](#会议收集篇)
    - [Elastrsearch 学习篇](#elastrsearch-学习篇)
    - [竞赛篇](#竞赛篇)
      - [【关于 NLP比赛】 那些你不知道的事 【点击查看详情】](#关于-nlp比赛-那些你不知道的事-点击查看详情)
      - [【关于 NLP 比赛方案学习】 那些你不知道的事](#关于-nlp-比赛方案学习-那些你不知道的事)
        - [【关于 NLP 比赛方案学习】 那些你不知道的事](#关于-nlp-比赛方案学习-那些你不知道的事-1)
    - [学习资源](#学习资源)
    - [NLP 数据集](#nlp-数据集)
    - [GCN_study学习篇](#gcn_study学习篇)
  - [参考资料](#参考资料)

## 介绍

### NLP 学习篇

#### 理论学习篇

##### [【关于 问答系统】 那些的你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/) 

###### [【关于 FAQ 】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/FAQ/)

- [【关于 FAQ Trick】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/FAQ/FAQ_trick/)
  - 一、动机
    - 1.1 问答系统的动机？
    - 1.2 问答系统 是什么？
  - 二、FAQ 检索式问答系统介绍篇
    - 2.1 FAQ 检索式问答系统 是 什么？
    - 2.2 query 匹配标准 QA 的核心是什么?
  - 三、FAQ 检索式问答系统 方案篇
    - 3.1 常用 方案有哪些？
    - 3.2 为什么 QQ 匹配比较常用？
      - 3.2.1 QQ 匹配的优点有哪些？
      - 3.2.2 QQ 匹配的语义空间是什么？
      - 3.2.3 QQ 匹配的语料的稳定性是什么？
      - 3.2.4 QQ 匹配的业务回答与算法模型的解耦是什么？
      - 3.2.5 QQ 匹配的新问题发现与去重是什么？
      - 3.2.6 QQ 匹配的上线运行速度是什么？
    - 3.3  QQ 匹配一般处理流程是怎么样？ 【假设 标准问题库 已处理好】
  - 四、FAQ 标准问题库构建篇
    - 4.1 如何发现 FAQ 中标准问题？
    - 4.2 FAQ 如何做拆分？
    - 4.3 FAQ 如何做合并？
    - 4.4 FAQ 标准库如何实时更新？
    - 4.5 FAQ 知识库搭建原则有哪些？
    - 4.6 FAQ 知识库应该具备哪些特点？
    - 4.7 FAQ 知识库应该怎么从零构建？
    - 4.8 FAQ 标准问题库答案如何优化？
    - 4.9 FAQ 怎样发现未能解决客户的问题？
- [【关于 Robust Industry-scale Question Answering System】 那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/FAQ/Industry-scaleQAS/)
  - 论文：Towards building a Robust Industry-scale Question Answering System
  -论文地址：https://www.aclweb.org/anthology/2020.coling-industry.9.pdf
  - 会议：COLING 2020
  - 工业规模的 NLP 系统需要两个功能。 
    - 1. 鲁棒性：“零样本迁移学习”(ZSTL) 的性能值得称道； 
    - 2. 效率：系统必须高效训练并即时响应。
  - 论文方法：介绍了一种称为GAAMA（Go Ahead Ask Me Anything）的生产模型的发展，它具有上述两个特征：
    - 为了稳健性，它在最近引入的Natural Questions（NQ）数据集上进行训练。 NQ 对 SQuAD 等旧数据集提出了额外的挑战：
      - (a) QA 系统需要阅读和理解整篇 Wikipedia 文章而不是一小段文章；
      - (b) NQ 在构建过程中不会受到观察偏差的影响，从而减少问题和问题之间的词汇重叠文章。 
    - GAAMA 由Attention-over-Attention、注意力头的多样性、分层迁移学习和合成数据增强组成，同时计算成本低廉。
  - 实验结果：
    - 建立在强大的 BERTQA 模型之上，GAAMA 在 F1 中比 NQ 上的行业规模最先进 (SOTA) 系统提供了 2.0% 的绝对提升；
    -  GAAMA 将零样本转移到了看不见的现实生活和重要领域，因为它在两个基准上产生了可观的性能：BioASQ 和新引入的 CovidQA 数据集。

- [【关于 LCNQA】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/LCNQA/)
  - 论文名称：Lattice CNNs for Matching Based Chinese Question Answering
- [LSTM-based Deep Learning Models for Non-factoid Answer Selection](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/FAQ/T1_LSTM-based_for_Non-factoid_Answer_Selection/)
- [【关于 Denoising Distantly Supervised ODQA】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/FAQ/T4_DenoisingDistantlySupervisedODQA/)
  - 论文名称：Denoising Distantly Supervised Open-Domain Question Answering
- [FAQ retrieval using query-question similarity and BERT-based query-answer relevance](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/FAQ/ACM2019_faq_bert-based_query-answer_relevance/)
- [【DC-BERT】 那些的你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/FAQ/SIGIR2020_DCBert/)
  - 论文名称：DC-BERT : DECOUPLING QUESTION AND DOCUMENT FOR EFFICIENT CONTEXTUAL ENCODING
  - 会议：SIGIR2020
  - 常用方法：
    - 遵循“检索和读取”管道，并使用基于BERT的重新排序器对检索到的文档进行筛选，
    - 然后再将其馈送到阅读器模块中。
    - BERT检索器将问题和每个检索到的文档的连接作为输入。
  - 问题：
    - 无法处理传入问题的高吞吐量，每个问题都有大量检索到的文档；
  - 论文方法：具有双重BERT模型的解耦上下文编码框架：
    - 一个在线BERT，仅对问题进行一次编码；
    - 一个正式的BERT，对所有文档进行预编码并缓存其编码；

###### [【关于 多轮检索 】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/mulFAQ/)

- [【关于 文本匹配和多轮检索】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/文本匹配和多轮检索.xmind)
- [【关于 MulFAQ】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/mulFAQ/)
  - [【关于 MSN】 那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/mulFAQ/MSN_mulQA/)
    - 论文名称：Multi-hop Selector Network for Multi-turn Response Selection in Retrieval-based chatbots
    - 论文地址：https://www.aclweb.org/anthology/D19-1011.pdf
    - 论文项目：https://github.com/chunyuanY/Dialogue
    - 动机：
      - 1. 上下文拼接问题：将候选回复与上下文utterance在多粒度级别进行匹配，这种方式忽略了使用过多的上下文信息带来副作用。
      - 2. 根据直接，一般来说距离回复越近的utterance，越能够反应最终轮对话的意图。所以，我们首先使用最后一个utterance作为key去选择word级别和sentence级别上相关的上下文回复。然而，我们发现**许多样本中最后一个utterance都是一些短句并且很多都是无效信息**（比如good, ok）
    - 方法：提出一种多跳选择网络（multi-hop selector network, MSN）
      - s1 ：采用 多跳选择器从 上下文集 中 选取最相关的上下文 utterances，并生成 k 个 不同的上下文；
      - s2 : 融合 k 个 上下文 utterance ，并与候选回复做匹配；
      - s3 : 匹配截取，采用 CNN 提取匹配特征，并 用 GRU 学习 utterance 间的临时关系；

###### [【关于 KBFAQ 】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/KBFAQ/)

- [【关于 KBFAQ】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/KBFAQ/)

##### [【关于 对话系统】 那些的你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/)

###### [【关于 自然语言理解 NLU】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/NLU/contextLU/)

- [【关于 上下文理解 contextLU】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/NLU/contextLU/)
- [【关于 DIET】 那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/NLU/DIET/)
  - 论文名称：DIET：Dual Intent and Entity Transformer
  - 作者：RASA
  - 论文代码：https://github.com/cheesama/DIET-pytorch 【韩文】
  - 动机：
    - 大规模的预训练语言模型在 GLUE 和 SuperGLUE 等语言理解基准上显示出令人印象深刻的结果，与分布式表示 (GloVe) 和纯监督方法等其他预训练方法相比有了显着改善。
  - 论文方法：我们介绍了 the Dual Intent and Entity Transformer (DIET) (DIET) 架构（基于两个任务共享的Transformer）：
    - 1 实体标签序列通过Transformer后，输出序列进入顶层条件随机场（CRF）标记层预测，输出每个Token成为BIOE的概率；
    - 2 完整话语和意图标签经过Transformer输出到单个语义向量空间中；
    - 3 利用点积损失最大化与目标标签的相似度，最小化与负样本的相似度。
  - 优点：
    - 它是一种模块化体系结构，适合典型的软件开发工作流程；
    - 在准确性和性能方面，能达到大规模预训练语言模型的效果；
    - 改进了现有技术，胜过当时的SOTA，并且训练速度提高了6倍。
- [【关于 Domain/Intent Classification 】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/NLU/IntentClassification/)
- [【关于 槽位填充 (Slot Filling)】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/NLU/SlotFilling/)

###### [【关于 状态追踪（DST）】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/DST/)

- [【关于 状态追踪（DST）】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/DST/)

###### [【关于 自然语言生成NLG 】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/NLG/)
- [【关于 自然语言生成NLG 】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/NLG/)
- [【关于 IRN 】 那些的你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/NLG/IRN/)
  - 论文：ScriptWriter: Narrative-Guided Script Generation
  - 发表会议：ACL2020
  - 论文地址：https://www.aclweb.org/anthology/2020.acl-main.10/
  - github：#
  - 论文动机：如何将输入中对话状态的slot-value对正确的在response生成
  - 论文方法：
    - 迭代网络：来不断修正生成过程不对的slot-value；
    - 强化学习：不断更新，实验证明我们的网络生成的回复中中slot关键信息生成的正确性大大提高。
  - 实验结果：对多个基准数据集进行了综合研究，结果表明所提出的方法显著降低了所有强基线的时隙错误率。人类的评估也证实了它的有效性。

###### [【关于 E2E 】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/E2E/)

- [【关于 TC_Bot(End-to-End Task-Completion Neural Dialogue Systems) 】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/E2E/TC_Bot/)
- [【关于 DF-Net 】 那些的你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/E2E/DynamicFusionNetwork/)
  - 论文：Dynamic Fusion Network for Multi-Domain End-to-end Task-Oriented Dialog
  - 发表会议：ACL2020
  - 论文地址：https://arxiv.org/abs/2004.11019
  - github：https://github.com/LooperXX/DF-Netmd
  - 论文动机：
    1. 依赖大量标准数据：端到端的模型依赖于大量的标注数据，这就导致了模型在一个新拓展的领域上很难利用。
    2. 对于一个新的领域，总是很难收集足够多的数据。这就使得将知识从具有充足标注数据的源领域迁移到一个只有少量标注数据的新领域成为非常重要的问题。
  - 前沿工作总结
    - 第一类：简单地结合多领域的数据集进行训练，如图 (a)
      - 优点：隐含地提取共享的特征
      - 缺点：很难有效捕捉领域特有的知识
    - 第二类是在各个领域单独地训练模型，如图 (b)
      - 优点：能够很好地捕捉领域特有的知识；
      - 缺点：却忽视了不同领域间共有的知识。
    - 第三类：通过建模不同领域间知识的连接来解决已有方法的局限。已有的一个简单的baseline如图 (c)，将领域共享的和领域私有的特征合并在一个共享-私有 (shared-private) 架构中。
      - 优点：区分了共享以及私有的知识
      - 缺点：
        - 一是面对一个几乎不具备数据的新领域时，私有模块无法有效提取对应的领域知识；
        - 二是这个架构忽略了一些领域子集间细粒度的想关性（比如和天气领域相比，导航领域和规划领域更相关）。
  - 思路：
  1. shared-private 架构：学习共享的知识以及对应的领域特有特征；
  2. 动态融合网络：动态地利用所有领域间的相关性提供给下一步细粒度知识迁移；
  3. 对抗训练 (adversarial training) ：促使共享模块生成领域共享特征

###### [【关于 Rasa 】 那些的你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/rasa/)

1. [【关于 rasa 安装 】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/rasa/rasa安装手册.md)
2. [【关于 rasa 基本架构 】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/rasa/rasa基本框架_视频讲解.md)
3. [【关于 rasa中文对话系统】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/rasa/rasa中文对话系统.md)
4. [【关于 rasa中文对话系统构建】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/rasa/rasa中文对话系统构建.md)
5. [【关于 rasa->NLU 】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/rasa/rasa系列/rasa_nlu.md)
6. [【关于 rasa -> Core -> FormAction 】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/rasa/rasa_core_FormAction/rasa_nlu.md)
7. [【关于 rasa -> Core -> Stories 】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/rasa/rasa系列/rasa_core_Stories.md)
8. [【关于 rasa -> Core -> Action 】那些你不知道的事](https://github.com/km1994/nlp_paper_study_qa/tree/master/QA_study/dialogue_system_study/rasa/rasa_core_FormAction/rasa_core_Action.md)


## 参考资料

1. [【ACL2020放榜!】事件抽取、关系抽取、NER、Few-Shot 相关论文整理](https://www.pianshen.com/article/14251297031/)
2. [第58届国际计算语言学协会会议（ACL 2020）有哪些值得关注的论文？](https://www.zhihu.com/question/385259014)
