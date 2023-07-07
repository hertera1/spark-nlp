---
layout: model
title: Chinese BertForTokenClassification Base Cased model (from ckiplab)
author: John Snow Labs
name: bert_token_classifier_base_chinese_pos
date: 2023-03-22
tags: [zh, open_source, bert, token_classification, ner, tensorflow]
task: Named Entity Recognition
language: zh
edition: Spark NLP 4.3.1
spark_version: 3.0
supported: true
engine: tensorflow
annotator: BertForTokenClassification
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained BertForTokenClassification model, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP. `bert-base-chinese-pos` is a Chinese model originally trained by `ckiplab`.

## Predicted Entities

`FW`, `Neqb`, `EXCLAMATIONCATEGORY`, `DE`, `Dk`, `COLONCATEGORY`, `VI`, `QUESTIONCATEGORY`, `DM`, `VF`, `VH`, `T`, `V_2`, `VE`, `Da`, `Cba`, `D`, `VD`, `Nd`, `A`, `SEMICOLONCATEGORY`, `Nv`, `VA`, `Neu`, `Nep`, `Nf`, `VC`, `Neqa`, `Di`, `PARENTHESISCATEGORY`, `Cbb`, `VL`, `VK`, `Nes`, `Nh`, `I`, `VG`, `VCL`, `DOTCATEGORY`, `SHI`, `PERIODCATEGORY`, `Na`, `Cab`, `PAUSECATEGORY`, `Caa`, `VAC`, `Ng`, `ETCCATEGORY`, `COMMACATEGORY`, `Ncd`, `Dfa`, `Nb`, `SPCHANGECATEGORY`, `P`, `Dfb`, `VHC`, `DASHCATEGORY`, `Nc`, `VB`, `VJ`

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/bert_token_classifier_base_chinese_pos_zh_4.3.1_3.0_1679492414087.zip){:.button.button-orange}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/bert_token_classifier_base_chinese_pos_zh_4.3.1_3.0_1679492414087.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

## How to use



<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}
```python
documentAssembler = DocumentAssembler() \
    .setInputCol("text") \
    .setOutputCol("document")

tokenizer = Tokenizer() \
    .setInputCols("document") \
    .setOutputCol("token")

tokenClassifier = BertForTokenClassification.pretrained("bert_token_classifier_base_chinese_pos","zh") \
    .setInputCols(["document", "token"]) \
    .setOutputCol("ner")

pipeline = Pipeline(stages=[documentAssembler, tokenizer, tokenClassifier])

data = spark.createDataFrame([["PUT YOUR STRING HERE"]]).toDF("text")

result = pipeline.fit(data).transform(data)
```
```scala
val documentAssembler = new DocumentAssembler()
    .setInputCol("text")
    .setOutputCol("document")

val tokenizer = new Tokenizer()
    .setInputCols("document")
    .setOutputCol("token")

val tokenClassifier = BertForTokenClassification.pretrained("bert_token_classifier_base_chinese_pos","zh")
    .setInputCols(Array("document", "token"))
    .setOutputCol("ner")

val pipeline = new Pipeline().setStages(Array(documentAssembler, tokenizer, tokenClassifier))

val data = Seq("PUT YOUR STRING HERE").toDS.toDF("text")

val result = pipeline.fit(data).transform(data)
```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|bert_token_classifier_base_chinese_pos|
|Compatibility:|Spark NLP 4.3.1+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[document, token]|
|Output Labels:|[ner]|
|Language:|zh|
|Size:|381.6 MB|
|Case sensitive:|true|
|Max sentence length:|128|

## References

- https://huggingface.co/ckiplab/bert-base-chinese-pos
- https://github.com/ckiplab/ckip-transformers
- https://muyang.pro
- https://ckip.iis.sinica.edu.tw
- https://github.com/ckiplab/ckip-transformers
- https://github.com/ckiplab/ckip-transformers