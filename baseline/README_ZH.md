[**English**](https://github.com/IIGROUP/AutoIE2/baseline) | [**中文**](https://github.com/IIGROUP/AutoIE2/baseline/README_ZH.md)

本目录是NLPCC-2021 Shared Task on AutoIE2: Sub-Event Identification任务的baseline。解决方案基于“UER: An Open-Source Toolkit for Pre-training Models”工作。在使用时请进行引用。

## 依赖环境
* Python >= 3.6
* torch >= 1.1
* six >= 1.12.0
* argparse
* packaging
* 如果使用混合精度，需要安装英伟达的apex
* 如果涉及到TensorFlow模型的转换，需要安装TensorFlow
* 如果在tokenizer中使用sentencepiece模型，需要安装[SentencePiece](https://github.com/google/sentencepiece)
* 如果使用模型集成stacking，需要LightGBM和[BayesianOptimization](https://github.com/fmfn/BayesianOptimization)
* 如果使用全词遮罩（whole word masking）预训练，需要分词工具，例如[jieba](https://github.com/fxsjy/jieba)

## 数据
* 将AutoIE2目录的taskdata路径下所有文件复制到此目录下的data文件夹中。
* 数据包括“COVID-19_train.tsv”，“Tokyo-Olympic-Games_train.tsv”，“Trade-War_train.tsv”，“unlabeled-corpus.tsv”。

## 快速上手
* 下载Google中文预训练模型[*google_zh_model.bin*](https://share.weiyun.com/A1C49VPb)，并将其放在 *models* 文件夹中。接着加载Google中文预训练模型。预训练模型由词向量层，编码层和目标任务层组成。
* 在下游分类数据集上微调预训练模型 *google_zh_model.bin*:
```
python3 run_classifier.py --pretrained_model_path models/google_zh_model.bin --vocab_path models/google_zh_vocab.txt \
                          --train_path [train_path] --dev_path [dev_path] --test_path [test_path] \
                          --epochs_num 3 --batch_size 32 --embedding word_pos_seg --encoder transformer --mask fully_visible
```
* 微调后的模型的默认路径是*models/finetuned_model.bin*, 然后利用微调后的分类器模型进行预测：
```
python3 inference/run_classifier_infer.py --load_model_path models/finetuned_model.bin --vocab_path models/google_zh_vocab.txt \
                                          --test_path [test_path] \
                                          --prediction_path data/prediction.tsv --labels_num 2 \
                                          --embedding word_pos_seg --encoder transformer --mask fully_visible
```
*--test_path* 指定需要预测的文件；<br>
*--prediction_path* 指定预测结果的文件；<br>
注意需要指定分类任务标签的个数 *--labels_num* ，这里是二分类任务。
注意在微调阶段使用 *--output_model_path* 指定微调后的模型的输出路径。预训练的实际batch size大小是 *--batch_size* 乘以 *--world_size*；分类的实际的batch size大小是 *--batch_size* 。

## 使用说明
项目组织如下：
```
UER-py/
    |--uer/
    |    |--encoders/ # 包括编码器模块，例如RNN, CNN, Transformer
    |    |--layers/ # 包括常用的神经网络层
    |    |--models/ # 包括 model.py，用于组合词向量（embedding）、编码器（encoder）、目标任务（target）模块
    |    |--utils/ # 包括常用的功能模块
    |    |--model_loader.py
    |    |--model_saver.py
    |    |--opts.py
    |
    |--datasets/ # 下游任务数据集存放文件夹
    |--models/ # 模型、词典、配置文件存放文件夹
    |--inference/ # 前向推理脚本存放文件夹
    |
    |--run_classifier.py # 分类脚本
    |--README.md
    |--README_ZH.md

```

## 引用
#### 如果您在您的学术工作中使用我们的工作（比如预训练模型权重），可以引用我们的[论文](https://arxiv.org/pdf/1909.05658.pdf)：
```
@article{zhao2019uer,
  title={UER: An Open-Source Toolkit for Pre-training Models},
  author={Zhao, Zhe and Chen, Hui and Zhang, Jinbin and Zhao, Xin and Liu, Tao and Lu, Wei and Chen, Xi and Deng, Haotang and Ju, Qi and Du, Xiaoyong},
  journal={EMNLP-IJCNLP 2019},
  pages={241},
  year={2019}
}
```
