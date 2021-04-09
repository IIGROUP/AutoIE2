# NLPCC-2021 Shared Task on AutoIE

## Background

Sub-events identification is a very fundamental problem in the field of information extraction, especially in emergency situations (e.g., terrorist attacks). Events usually evolve rapidly and therefore, successive sub-events occur. How to efficiently identify the target sub-events from large volume of related data is very challenging. Moreover, usually a limited amount of labelled seed data is given, and annotating large size dataset is expensive and time consuming. Thus, a generic solution for sub-event identification cannot rely on the hypothesis that enough labelled data is provided.

## Task

The goal of this task is to build an IE system that can quickly adapt to a new occurring sub-event. Specifically, given a large number of event related corpus and a few labelled seed data, the task aims to build an IE system which may identify the target sub-events. Besides the machine learning model designing, annotating data selected from the unlabeled corpus is also allowed, but the size of the labelled data is fixed. How to select the best data to annotate is also an important step in this task. The task setting is very practical and thus the proposed solutions may generalize well in real world applications.

Note:  
1.	Three sub-events would be presented in the task and will be released with the seed dataset.
2.	human annotation and correction are allowed for training dataset which is composed of seedset and data annotated by participants from unlabeled corpus. 
3.	The size of data annotated by participants may not exceed 1000 per sub-event .

## Data
All corpora provided are obtained from comment scenes (generally 8 to 120 characters long). The corpora are split into three parts, i.e., unlabeled dataset, seed dataset and test dataset. Participants can use the first two datasets to construct their own training set to train IE model, and use the testing dataset for evaluation. More details about these three datasets are as follows:

Unlabelled dateset: 100,000 samples related to the sub-events.

Seed dataset: 200 labeled samples per sub-event. 

Test dataset : 2000 labeled samples per sub-event.

Tip: the exact size of these three datasets will be released by 2021/4/30 

## Submission & Evaluation

For submission, please write the prediction result into a single file and email it to Xingyu Bai
bxy20@mails.tsinghua.edu.cn

there are two setting for this evaluation task:

S1: training data size may not exceed N1 like 200 per sub-event, which is designed for few sample problem

S2: training data size which is composed of seedset and data annotated from unlabeled corpus may not exceed N2 like 1200, which is designed for data selection problem.

The submission file format should be the same as the format of given seed dataset. To be specific, each sample in the test dataset is labelled by 3, 2, 1 and 0. 

the final evaluation leadboard is the average accuracy of two settings

Ranking of submissions are based on the the final evaluation.

A eval.py script is provided to calculate the accuracy and valid prediction format. 


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

