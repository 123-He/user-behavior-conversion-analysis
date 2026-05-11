# 用户行为转化分析项目

## 1. 项目简介

本项目基于电商用户行为数据，围绕用户从浏览到购买的完整转化链路，完成数据清洗、漏斗分析、用户意图评分、购买预测建模和样本不平衡优化。

项目核心目标是：

- 识别用户在「点击 → 收藏 → 加购 → 购买」链路中的主要流失环节；
- 构建高意图用户识别规则，提升后续购买用户召回能力；
- 通过机器学习模型预测用户未来 3 天购买概率；
- 对比不同建模方案在真实不平衡样本下的效果，避免离线指标虚高。

## 2. 项目亮点

- 构建「点击 → 收藏 → 加购 → 购买」转化漏斗，定位整体购买转化率低于 3%，主要流失集中在点击到收藏/加购阶段；
- 基于 RF 分层、近活跃候选池和时间衰减权重构建高意图评分，Top10% 用户后续购买率达到 8.7%，高于 RF 基线 5.6% 和随机基线 2.8%；
- 构建用户未来 3 天购买预测模型，对比决策树、随机森林和 LightGBM，最终 LightGBM 在验证集上达到 AUC 0.78、PR-AUC 0.36、Top10% 用户购买率 9.8%；
- 针对正负样本约 1:7 的不平衡问题，对比 SMOTE 与类权重方案，最终保留类权重 + 时间切分验证方案，更贴近真实营销场景。

## 3. 项目结构

```text
user-behavior-conversion-analysis/
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   ├── raw/
│   │   └── sample_user_behavior.csv
│   └── processed/
├── notebooks/
│   └── user_behavior_analysis.ipynb
├── src/
│   ├── data_cleaning.py
│   ├── funnel_analysis.py
│   ├── intent_score.py
│   ├── train_model.py
│   └── utils.py
├── outputs/
│   ├── figures/
│   └── reports/
└── docs/
    └── project_summary.md