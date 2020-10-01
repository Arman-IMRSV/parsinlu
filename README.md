# ParsiGLUE
 - intro and what it is 
 - where to download the data 


## Baselines  
 - Download the data and include it in the `data/` directory.  
 - See the relevant section on how to train models for each task:   
    * [Textual entailment](#textual-entailment) 
    * [Query Paraphrasing](#query-paraphrasing) 
    * [Reading Comprehension](#reading-comprehension)
    * [Multiple-choice QA](#multiple-choice-qa)
    * [Machine Translation](#machine-translation) 
    * [Sentiment Analaysis](#sentiment-analysis) 
   
If you're using a GPU, make sure that you set the appropriate enviromental variable. For example: 
```bash
export CUDA_VISIBLE_DEVICES=0
```    
   
### Textual Entailment 
Textual Entailment is the task of deciding whether a  whether two given questions are paraphrases of each other or not. 

Here is an example: 



 This example code fine-tunes mBERT (multi-lingual BERT) on the this task. 
 It runs in xxx mins on a single tesla V100 16GB. 

```bash 
export DATA_DIR=data/entailment

python run_text_classification.py \
  --data_dir $DATA_DIR \
  --task_name entailment \
  --model_name_or_path bert-base-multilingual-cased \
  --do_train \
  --do_eval \
  --learning_rate 5e-5 \
  --num_train_epochs 2.0 \
  --max_seq_length 128 \
  --output_dir /tmp/debug_qqp/ \
  --save_steps -1
```

--per_device_train_batch_size 8 \

Training with the previously defined hyper-parameters yields the following results on the test set:
 
```
acc = ?
```
 
 ### Query Paraphrasing 
 QQP is the task of detecting whether two given questions are paraphrases of each other or not. 

|  Label | Question 1 | Question 2 |
| :---: | :---: | :---: |
|  not-paraphrase | <p dir='rtl' align='right'>さ あ ひ る به چه معنی است؟</p>  | <p dir='rtl' align='right'> &脑 洞 大 به چه معنی است؟</p> |
|  paraphrase | <p dir='rtl' align='right'> قانون سوم حرکت نیوتن چیست؟ آیا می توانید یک عمل و یک عکس العمل را با مثال توضیح دهید؟ </p>| <p dir='rtl' align='right'> آیا کسی می تواند قانون سوم حرکت نیوتون را توضیح دهد؟ </p> |
|  not-paraphrase | <p dir='rtl' align='right'> آیا لیزر موهای زائد باعث فرار دائمی از موهای ناخواسته می شود؟ </p>| <p dir='rtl' align='right'> آیا لیزر موهای زائد دائمی است؟ </p> |
|  paraphrase | <p dir='rtl' align='right'> چه شانس هایی وجود دارد که اگر هیلاری در انتخابات رأی عمومی به پیروزی برسد ، کالح انتخاباتی بر ضد ترامپ تصمیم بگیرد؟ </p>|<p dir='rtl' align='right'> این احتمال وجود دارد که در ۱۹ دسامبر ، کالج انتخاباتی بتواند دونالد ترامپ را از دور خارج کند و به هیلاری کلینتون رأی دهد؟ </p> |

 This example code fine-tunes mBERT (multi-lingual BERT) on the this task. 
 It should not take more than 30 mins on a single V100 12GB. 

```bash 
export DATA_DIR=data/qqp

python run_text_classification.py \
  --data_dir $DATA_DIR \
  --task_name qqp \
  --model_name_or_path bert-base-multilingual-cased \
  --do_train \
  --do_eval \
  --learning_rate 5e-5 \
  --num_train_epochs 2.0 \
  --max_seq_length 128 \
  --output_dir /tmp/debug_qqp/ \
  --save_steps -1
```

--per_device_train_batch_size 8 \

Training with the previously defined hyper-parameters yields the following results on the test set:
 
```
acc = ?
```
 
 ### Reading Comprehension 
 TODO 
 
 ### Multiple-Choice QA 
 TODO 
 
 ### Machine Translation 
 TODO 
 
 ### Sentiment Analysis 
TODO 

## Citation 
If you find this work useful please cite the following work: 
```bibtex 
@article{2020parsiglue,
    title={},
    author={},
    journal={arXiv},
    year={2020}
}
```