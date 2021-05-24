### SparkML 和SparkMLlib 区别

- spark mllib 基于RDD
  - 数据准备 需要创建一个 基于LabeledPoint的RDD
  - LabeledPoint（目标，[特征]）
  - 已经停止更新了 处于维护状态
- spark ML 基于dataframe
  - 数据准备 需要把所有的特征放到一列中 dataframe还需要有一列是 目标值
  - model = lr.setLabelCol('affairs').setFeaturesCol('feautures').fit(trainDF)
  - spark ML 与 sklearn更类似
  - 最新的API放到 spark ML中的