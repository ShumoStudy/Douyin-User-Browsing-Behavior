使用数据集 https://drive.google.com/file/d/1ukNZmei7VNwwaZnYJ2xRefjp_s0bOzQa/view?usp=drive_link


部分示例数据

![image](https://github.com/user-attachments/assets/3d173933-823e-40e7-a32b-fb43372d9404)


初始数据

![image](https://github.com/user-attachments/assets/ebdc83e6-9e0c-4540-acdd-a39591677223)


获取数据的维度和数量：1737312 rows × 13 columns

![image](https://github.com/user-attachments/assets/9240415f-688e-457e-88a2-febaa90a68f7)


使用正则表达式查看时间数据的规范性

将时间的数据类型从 object 修改为 datetime 类型

查看清洗完后的数据信息


![image](https://github.com/user-attachments/assets/7115b67e-6ab6-4d7a-96a0-2082025e346f)


根据已有字段可以可以从浏览行为中抽象出：用户、作品、作者、音乐、城市等实体，在本项目中，我们仅对用户、作者和作品角度进行简单分析，并加入一些数据分析方法

作品时长是一个对用户点赞有影响的特征，，从图中可以看出存在部分数据可视化后是异常点，需要处理，总体来说大部分数据都集中在0-100


![image](https://github.com/user-attachments/assets/b7da58e7-1b4d-4b5e-8927-86b3028f35ba)


![image](https://github.com/user-attachments/assets/df915a41-ce9d-435d-8c1a-c30ebfaa6910)


每一条数据都是由用户主动发起的，与创作者视频进行交互的行为记录。站在用户的角度，涉及到浏览量，点赞量，浏览的作品、作者、BGM的总数等，拟定统计指标如下：


![image](https://github.com/user-attachments/assets/272b4d0a-8f0b-4af1-9b58-b92c798b9c44)


站在作者的角度，涉及到总浏览量，总点赞量，总作品数等，拟定指标如下：

![image](https://github.com/user-attachments/assets/54dee060-9e8a-408b-bee3-b3194342a923)

站在作品的角度，涉及到点赞量，浏览量，背景音乐等，拟定统计指标如下：

![image](https://github.com/user-attachments/assets/443fe88a-dc0d-410e-8414-9b33c18229de)

使用Pyecharts库和Matplotlib进行数据的可视化

用户点赞量与浏览量对比

![image](https://github.com/user-attachments/assets/55ef7340-d66b-4121-9d0d-49ab58ad607f)

背景音乐点赞量与浏览量对比

![image](https://github.com/user-attachments/assets/ee68040b-976a-49cf-9d66-f27387424bff)

作品不同发布时间用户点赞情况

可以看出不同发布时间点赞量存在一定规律，符合当下上班族作息，晚上发布的视频在第二天被刷到、点赞

![image](https://github.com/user-attachments/assets/aec23130-2652-4ca9-8a94-4bcf9d27ba83)

2.	40天点赞情况

可以看出40天内有一段时间点赞量处于比较高的水平

![image](https://github.com/user-attachments/assets/c8a1ff0a-f8c3-4ec3-910d-266ebfe8b691)

6.	40天看完视频与浏览视频对比

可以看出用户刷到的视频不一定都符合用户喜好

![image](https://github.com/user-attachments/assets/83c295b0-45fd-4046-886f-0609ef5adfcb)

7.	作者地区与用户地区分布关系

可以看出每个用户观看的作品来自各个地区

![image](https://github.com/user-attachments/assets/6f3731f4-b044-4751-a73a-41691d124b83)

8.	一周内播放分布图

可以看出一周内的播放差距不大

![image](https://github.com/user-attachments/assets/f9c07168-43c4-4a80-a889-b3996a6ce5d0)

9.	不同浏览量用户占比

可以看出浏览0-5个视频和10-25个视频用户最多

![image](https://github.com/user-attachments/assets/7b0f5252-8cb1-474b-8dfa-b3a7dc9e31d1)

10.	用户完整观看情况

可以看出用户完整观看视频数量大多在0-5，部分用户观看视频时不会看完

![image](https://github.com/user-attachments/assets/1f6ca022-b1a0-4a4f-aed9-2dd812c448c6)

11.	播放量top10作者所在城市分布

可以看出用户刷到相同城市作品具有倾向性，部分城市作品播放量较高

![image](https://github.com/user-attachments/assets/497d2f3c-4d35-4a41-93d6-a443441f3edd)



12.	作品点赞分布
点赞数量是6-40，大部分点赞数都集中在6-10，0-5点赞数更多，可以看出用户刷到视频不点赞居多

![image](https://github.com/user-attachments/assets/519039cb-0a97-4169-8cdf-5e9ab3e99524)



13.	浏览量与点赞量热力分布图

可以看出浏览量在0-100点赞量在-1-0集中的比较多

![image](https://github.com/user-attachments/assets/117ec7ce-fc63-443a-a368-042d0c1d393c)

5.2.1 数据建模与评估

在数据建模时，进行了逻辑回归、决策树、随机森林、朴素贝叶斯和XGBoost建模

首先对数据特征进行分析，得到特征相关性热力图，可以看出item_id和author_id这两个特征相关性最高

![image](https://github.com/user-attachments/assets/ac04e32c-a645-44c2-90ff-022dde1b2061)

然后再预测各模型准确率，可以看出各模型准确率都比较高

![image](https://github.com/user-attachments/assets/2966cc94-590a-4db1-bad2-6084f136348a)

再来看看各模型ROC曲线和AUC值，可以看出随机森林AUC值最高，效果最好



![image](https://github.com/user-attachments/assets/d96e1ba8-95f6-465d-93b7-2a671df74aa4)

由上面的图可以看出特征中item_id和author_id两个特征相关性较高，说明用户刷到视频时会看创作者以及作品的名字，如果是较为关注的创作者或作品，则点赞的概率比普通的要高，所以把握用户的兴趣爱好应该是创作者要注意的一点。

在对用户、作者、作品进行简单的描述性统计分析与可视化展示后，我们尝试通过一些数据挖掘方法对数据进一步探究

用户聚类k值选择：通过综合肘部法则和sc值，选择k=4作为用户聚类模型

![image](https://github.com/user-attachments/assets/a86bead7-9cc4-4cfb-92e0-f80e754e7eac)

将用户聚类分成四类，可以看出一类用户占比最多，达到了70.48%，而四类用户最少，只有0.99%

![image](https://github.com/user-attachments/assets/c62bfcdd-a134-400d-bbc3-10c1981b84ce)

作者聚类k值选择：通过综合肘部法则和sc值，选择k=4作为作者聚类模型

![image](https://github.com/user-attachments/assets/093dc055-9df8-4efb-a967-11a3a978d38c)

将作者聚类分为四类，一类作者最多

![image](https://github.com/user-attachments/assets/e1d7b503-bf4b-4b66-9671-91ccca232782)





















