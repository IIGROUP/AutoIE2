# NLPCC-2021 Shared Task on AutoIE2: Sub-Event Identification

## Leaderboard with Few Sample
| Rank | TeamName | Organization | Acc-score |
| :-----: | :----: | :----: | :----: |
| 1 | HUMAN | NLPCC | 86.33 |
| 2 | BIT-Event | Beijing Institute of Technology | 79.13 |
| 3 | happy | Northeastern University | 77.98 |
| 4 | Real | Waseda University | 77.40 |
| 5 | Alphonse | Harbin Institute of Technology, Shenzhen | 76.22 |
| 6 | ZM | CUG | 76.01 |
| 7 | The Brainiacs | 中国人民大学 | 75.00 |
| 8 | guagua | Tianjin University | 74.95 |
| 9 | JHX | China University of Geosciences (Beijing) | 74.91 |
| 10 | CC | Renmin University | 74.88 |
| 11 | CUGB1012 | China University of Geosciences | 74.65 |
| 12 | ZZN | 中国地质大学 | 74.53 |
| 13 | 52wtq | NanChang Hangkong University | 74.25 |
| 14 | buaa_iip | Beihang University | 73.28 |
| 15 | IE_X | 北京理工大学 | 57.15 |
| 16 | BaselineSystem | NLPCC | 70.52 |


## Leaderboard with Data Selection
| Rank | TeamName | Organization | Acc-score |
| :-----: | :----: | :----: | :----: |
| 1 | HUMAN | NLPCC | 86.33 |
| 2 | BIT-Event | Beijing Institute of Technology | 79.10 |
| 3 | happy | Northeastern University | 76.50 |
| 4 | guagua | Tianjin University | 76.08 |
| 5 | Alphonse | Harbin Institute of Technology, Shenzhen | 76.05 |
| 6 | CC | Renmin University | 74.72 |
| 7 | The Brainiacs | 中国人民大学 | 74.42 |
| 8 | CUGB1012 | China University of Geosciences | 74.35 |
| 9 | 52wtq | NanChang Hangkong University | 73.73 |
| 10 | JHX | China University of Geosciences (Beijing) | 73.68 |
| 11 | Real | Waseda University | 73.38 |
| 12 | buaa_iip | Beihang University | 73.18 |
| 13 | IE_X | 北京理工大学 | 67.22 |
| 14 | BaselineSystem | NLPCC | 70.85 |


## Overall Leaderboard
| Rank | TeamName | Organization | Acc-score |
| :-----: | :----: | :----: | :----: |
| 1 | HUMAN | NLPCC | 86.33 |
| 2 | BIT-Event | Beijing Institute of Technology | 79.12 |
| 3 | happy | Northeastern University | 77.24 |
| 4 | Alphonse | Harbin Institute of Technology, Shenzhen | 76.14 |
| 5 | guagua | Tianjin University | 75.52 |
| 6 | Real | Waseda University | 75.39 |
| 7 | CC | Renmin University | 74.80 |
| 8 | The Brainiacs | 中国人民大学 | 74.71 |
| 9 | CUGB1012 | China University of Geosciences | 74.50 |
| 10 | JHX | China University of Geosciences (Beijing) | 74.30 |
| 11 | 52wtq | NanChang Hangkong University | 73.99 |
| 12 | ZM | CUG | 73.43 |
| 13 | buaa_iip | Beihang University | 73.23 |
| 14 | ZZN | 中国地质大学 | 72.69 |
| 15 | IE_X | 北京理工大学 | 62.19 |
| 16 | BaselineSystem | NLPCC | 70.69 |


## Background

Sub-events identification is a very fundamental problem in the field of information extraction, especially in emergency situations (e.g., terrorist attacks). It is challenging for two reasons:
1.	data confusing and imbalance. Events usually evolve rapidly and successive sub-events occur. Only a few target sub-events data need to be identifid from the large volume of events related data.
2.	low resource. Usually only a limited amount of labelled seed data is given for learning and more annotating datasets are expensive and time consuming.

However, the existing works cannot fully meet the requirements, and thus better few shot learning and data selection models for sub-event identification are crucial.


## Task

The goal of this task is to build an IE system (Information Extraction system) that can quickly adapt to a new occurring sub-event. Specifically, there are two settings of this task:
1.	Given a large number of event-related corpus and a few labelled seed data, the task aims to build an IE system which may identify the target sub-events.
2.	Besides the machine learning model designing, annotating data selected from the unlabeled corpus is also allowed, but the size of the labelled data from the unlabeled corpus is fixed. How to select the best data to annotate and supply training dataset is also an important step in this task.

The task settings are very practical, thus the proposed solutions may generalize well in real world applications.

Note:  
1.	Three sub-event would be presented in the task and will be released with the seed dataset.
2.	Human annotation and correction are allowed for training dataset which is composed of seedset and data annotated by participants from unlabeled corpus. 
3.	The size of data annotated by participants may not exceed 100 per sub-event.


## Data
All corpus provided are obtained from comments (generally 8 to 120 characters long). The corpus are split into three parts, i.e., unlabeled dataset, seed dataset and testing dataset. The  labelled seed dataset(100 samples per event) and unlabeled dataset(100K for 3 events) are released to participants to construct their own training set and developing set, and the testing dataset(around 2k per event) is used for final evaluation.

More details about these three datasets are as follows:
1.	Unlabelled dateset: totally 100,000 samples related to the three sub-events.
2.	Seed dataset: 100 labeled samples per sub-event. 
3.	Test dataset : 2000 labeled samples per sub-event.

Tip: Testset will be released untill 2021/6/5.


## Submission & Evaluation

For submission, please write the prediction result into a single file and email it to Xingyu Bai
bxy20@mails.tsinghua.edu.cn

There are two settings for this evaluation task and the final evaluation is the average accuracy of two settings;
1.	few sample problem setting: the size of training data may not exceed 100 per sub-event, human annotation is not allowed.
2.	data selection problem setting: human annotation is allowed. The size of training data which is composed of seedset and data annotated from unlabeled corpus may not exceed 200.

The format of submission file should be the same as the format of given submission-format.txt file under taskdata folder. To be specific, each sample in the test dataset is labelled by 3, 2, 1 and 0, which represent Trade War, Tokyo Olympic Games, COVID-19 and negative samples, respectively.

An eval.py script is provided to calculate the accuracy and verify prediction format. 



## Prizes

This task will award prizes for top 3 teams. Winners will get the award certificates issued by NLPCC and CCF Technical Committee on Chinese Information Technology. 


First prize:         5000 RMB + award certificate

Second prize:        3000 RMB + award certificate

Third prize:         1000 RMB + award certificate


## Website

Further arrangement and baseline system will be published in https://github.com/IIGROUP/AutoIE2

## Organizers: 

Xuefeng Yang 

email: yang0302@e.ntu.edu.sg

Weigang Guo 

email: springwg@163.com

Xingyu Bai (Tsinghua University, Shenzhen International Graduate School)

email: bxy20@mails.tsinghua.edu.cn

Yujiu Yang (Tsinghua University, Shenzhen International Graduate School)

email: yang.yujiu@sz.tsinghua.edu.cn

