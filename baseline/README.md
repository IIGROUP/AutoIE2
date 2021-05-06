[**English**](https://github.com/IIGROUP/AutoIE2/blob/main/baseline/README.md) | [**中文**](https://github.com/IIGROUP/AutoIE2/blob/main/baseline/README_ZH.md)

This repository is the baseline for the AutoIE2 evaluation. The solution is based on the work “UER: An Open-Source Toolkit for Pre-training Models”. Please cite it if you use it. 

## Requirements
* Python 3.6
* torch >= 1.1
* six >= 1.12.0
* argparse
* packaging
* For the mixed precision training you will need apex from NVIDIA
* For the pre-trained model conversion (related with TensorFlow) you will need TensorFlow
* For the tokenization with sentencepiece model you will need [SentencePiece](https://github.com/google/sentencepiece)
* For developing a stacking model you will need LightGBM and [BayesianOptimization](https://github.com/fmfn/BayesianOptimization)
* For the pre-training with whole word masking you will need word segmentation tool such as [jieba](https://github.com/fxsjy/jieba)

## Data
* Please copy all the files and folder under taskdata path in the AutoIE2 repository into the data folder under this repository.
* Data include the "COVID-19_train.tsv", "Tokyo-Olympic-Games_train.tsv", "Trade-War_train.tsv", "unlabeled-corpus.tsv".

## Quickstart
* Download Google's original pre-trained Chinese BERT model [*google_zh_model.bin*](https://share.weiyun.com/A1C49VPb) (in UER's format), and put it in *models* folder. Load the pre-trained Chinese BERT model. Pre-training model is composed of embedding, encoder, and target.
* Then fine-tune pre-trained models *google_zh_model.bin* on downstream classification dataset:
```
python3 run_classifier.py --pretrained_model_path models/google_zh_model.bin --vocab_path models/google_zh_vocab.txt \
                          --train_path [train_path] --dev_path [dev_path] --test_path [test_path] \
                          --epochs_num 3 --batch_size 32 --embedding word_pos_seg --encoder transformer --mask fully_visible
```
The default path of the fine-tuned classifier model is *models/finetuned_model.bin* . Then do inference with the fine-tuned model. 
```
python3 inference/run_classifier_infer.py --load_model_path models/finetuned_model.bin --vocab_path models/google_zh_vocab.txt \
                                          --test_path [test_path] \
                                          --prediction_path data/prediction.tsv --labels_num 2 \
                                          --embedding word_pos_seg --encoder transformer --mask fully_visible
```
*--test_path* specifies the path of the file to be predicted. <br>
*--prediction_path* specifies the path of the file with prediction results. <br>
Need to explicitly specify the number of labels by *--labels_num*. Here is a two-way classification dataset.
Notice that explicitly specify the fine-tuned model path by *--output_model_path* in fine-tuning stage. The actual batch size of pre-training is *--batch_size* times *--world_size* ; The actual batch size of classification is *--batch_size* . 

## Instructions
UER-py is organized as follows：
```
UER-py/
    |--uer/
    |    |--encoders/ # contains encoders such as RNN, CNN, Transformer
    |    |--layers/ # contains frequently-used NN layers, such as embedding layer, normalization layer
    |    |--models/ # contains model.py, which combines embedding, encoder, and target modules
    |    |--utils/ # contains frequently-used utilities
    |    |--model_loader.py
    |    |--model_saver.py
    |    |--opts.py
    |
    |--datasets/ # contains downstream tasks
    |--models/ # contains pre-trained models, vocabularies, and configuration files
    |--inference/ # contains inference scripts for downstream tasks
    |
    |--run_classifier.py # classification
    |--README.md
    |--README_ZH.md

```

## Citation
#### If you are using the work (e.g. pre-trained model) in UER-py for academic work, please cite the [system paper](https://arxiv.org/pdf/1909.05658.pdf) published in EMNLP 2019:
```
@article{zhao2019uer,
  title={UER: An Open-Source Toolkit for Pre-training Models},
  author={Zhao, Zhe and Chen, Hui and Zhang, Jinbin and Zhao, Xin and Liu, Tao and Lu, Wei and Chen, Xi and Deng, Haotang and Ju, Qi and Du, Xiaoyong},
  journal={EMNLP-IJCNLP 2019},
  pages={241},
  year={2019}
}
```
