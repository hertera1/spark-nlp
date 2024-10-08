---
layout: model
title: English RoBertaForSequenceClassification Cased model (from kco4776)
author: John Snow Labs
name: roberta_classifier_soongsil_bert_wellness
date: 2023-11-29
tags: [en, open_source, roberta, sequence_classification, classification, onnx]
task: Text Classification
language: en
edition: Spark NLP 5.2.0
spark_version: 3.0
supported: true
engine: onnx
annotator: RoBertaForSequenceClassification
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained RoBertaForSequenceClassification model, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP. `soongsil-bert-wellness` is a English model originally trained by `kco4776`.

## Predicted Entities

`일반대화`, `부가설명`, `상태`, `원인`, `자가치료`, `내원이유`, `모호함`, `배경`, `감정`, `증상`, `현재상태`, `치료이력`

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/roberta_classifier_soongsil_bert_wellness_en_5.2.0_3.0_1701236076612.zip){:.button.button-orange.button-orange-trans.arr.button-icon}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/roberta_classifier_soongsil_bert_wellness_en_5.2.0_3.0_1701236076612.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

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

seq_classifier = RoBertaForSequenceClassification.pretrained("roberta_classifier_soongsil_bert_wellness","en") \
    .setInputCols(["document", "token"]) \
    .setOutputCol("class")

pipeline = Pipeline(stages=[documentAssembler, tokenizer, seq_classifier])

data = spark.createDataFrame([["PUT YOUR STRING HERE"]]).toDF("text")

result = pipeline.fit(data).transform(data)
```
```scala
val documentAssembler = new DocumentAssembler()
      .setInputCols(Array("text"))
      .setOutputCols(Array("document"))

val tokenizer = new Tokenizer()
    .setInputCols("document")
    .setOutputCol("token")

val seq_classifier = RoBertaForSequenceClassification.pretrained("roberta_classifier_soongsil_bert_wellness","en")
    .setInputCols(Array("document", "token"))
    .setOutputCol("class")

val pipeline = new Pipeline().setStages(Array(documentAssembler, tokenizer, seq_classifier))

val data = Seq("PUT YOUR STRING HERE").toDS.toDF("text")

val result = pipeline.fit(data).transform(data)
```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|roberta_classifier_soongsil_bert_wellness|
|Compatibility:|Spark NLP 5.2.0+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[document, token]|
|Output Labels:|[class]|
|Language:|en|
|Size:|368.7 MB|
|Case sensitive:|true|
|Max sentence length:|256|

## References

References

- https://huggingface.co/kco4776/soongsil-bert-wellness
- https://github.com/jason9693/Soongsil-BERT