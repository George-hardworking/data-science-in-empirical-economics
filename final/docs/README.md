# 项目名称：基于机器学习的 A 股上市公司财务困境预测与特征归因
**Project Title: Predicting Financial Distress in China's A-Share Market: A Machine Learning Approach with Feature Attribution**

## 1. 项目概览 (Project Overview)
本项目是《实证经济学中的数据科学》课程的期末研究。项目旨在探讨一个经典的实证金融问题：**公开的财务报表数据是否蕴含了足以提前预测企业陷入财务困境（被实施 ST/退市风险警示）的非线性信号？**

传统实证经济学多采用 Logistic 回归（如 Altman Z-score 模型）进行线性推断。本项目将引入以随机森林（Random Forest）和 XGBoost 为代表的树模型机器学习算法，探索复杂财务指标间的非线性交叉效应，并通过特征重要性（Feature Importance）分析，为投资者预警和监管机构排雷提供经验证据。

## 2. 目录结构与开发规范 (Directory Structure & Setup)
智能体（Agent）在执行代码编写时，请严格遵守以下本地目录结构。所有 Python 代码必须在 `scripts/final.ipynb` 中以 Jupyter Notebook 的单元格（Cell）形式逐步实现。

```text
data-science-in-empirical-economics/
└── final/
    ├── docs/       # 存放本文档 (README.md) 及参考文献
    ├── output/     # 存放代码运行生成的清洗后数据、模型文件及可视化图表 (PNG/PDF)
    ├── raw/        # 存放通过 AkShare 抓取的原始 CSV 数据
    └── scripts/    # 存放核心代码文件 final.ipynb