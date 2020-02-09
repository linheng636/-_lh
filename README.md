数据来源：
=======
租房网北京出租房源共计4245条信息
房源属性：楼盘名称，租赁方式；面积；朝向；房租；城市；区域；街道或片区；地址；公交站等。

问题及解决方案：
==========

1)通过数据概览，发现存在数据不干净，字段少等问题需要进行数据清理。
------
*数值型变量中包含字符串内容导致数据类型为object，需要将数值信息与字符信息分离并重新整合。
*朝南变量大部分为单一值，近似于零方差向量。
*查看缺失值分布，根据缺失值重要性等因素进行填充或删除处理。

2)如何根据小区名称关联更多地理特征来提高模型泛化能力？
-------
*通过xgeocoding定位小区名称可以获得小区的经纬度。
*通过request爬取百度开发者平台数据或者小区周边POI信息，构建新特征
*本例获取了小区周边500米内便利店数量构造新特征

3)如何进行数据预处理？
----------------
*以每平米租金为因变量
*利用箱型图查看数据分布，并根据3α原则处理异常值

4)选取不同的模型进行模型训练并对比模型效果，确定最终预测模型
------------------
*使用留一法法对数据集进行划分，验证集比例为30%
*分别建立lassocv及xgboost模型进行训练，并对比模型效果，并对模型进行保存
*根据xgboost模型查看特征重要性

