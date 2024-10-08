---
layout: model
title: Turkish BertForSequenceClassification Uncased model (from sfurkan)
author: John Snow Labs
name: bert_classifier_lex_textclassification_turkish_uncased
date: 2023-10-31
tags: [bert, sequence_classification, classification, open_source, tr, onnx]
task: Text Classification
language: tr
edition: Spark NLP 5.1.4
spark_version: 3.4
supported: true
engine: onnx
annotator: BertForSequenceClassification
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained BertForSequenceClassification model, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP. `LexBERT-textclassification-turkish-uncased` is a Turkish model originally trained by `sfurkan`.

## Predicted Entities

`Genelge`, `Tüzük`, `Kanun Hükmünde Kararname`, `Yönetmelik`, `Özelge`, `Cumhurbaşkanlığı Kararnamesi`, `Kanun`, `Komisyon Raporu`, `Tebliğ`, `Resmi Gazete`

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/bert_classifier_lex_textclassification_turkish_uncased_tr_5.1.4_3.4_1698786403966.zip){:.button.button-orange.button-orange-trans.arr.button-icon}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/bert_classifier_lex_textclassification_turkish_uncased_tr_5.1.4_3.4_1698786403966.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

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

sequenceClassifier_loaded = BertForSequenceClassification.pretrained("bert_classifier_lex_textclassification_turkish_uncased","tr") \
    .setInputCols(["document", "token"]) \
    .setOutputCol("class")

pipeline = Pipeline(stages=[documentAssembler, tokenizer,sequenceClassifier_loaded])

data = spark.createDataFrame([["Spark NLP'yi seviyorum"]]).toDF("text")

result = pipeline.fit(data).transform(data)
```
```scala
val documentAssembler = new DocumentAssembler() 
          .setInputCol("text") 
          .setOutputCol("document")

val tokenizer = new Tokenizer() 
    .setInputCols(Array("document"))
    .setOutputCol("token")

val sequenceClassifier_loaded = BertForSequenceClassification.pretrained("bert_classifier_lex_textclassification_turkish_uncased","tr") 
    .setInputCols(Array("document", "token")) 
    .setOutputCol("class")

val pipeline = new Pipeline().setStages(Array(documentAssembler, tokenizer,sequenceClassifier_loaded))

val data = Seq("Spark NLP'yi seviyorum").toDF("text")

val result = pipeline.fit(data).transform(data)
```

{:.nlu-block}
```python
import nlu
nlu.load("tr.classify.bert.uncased").predict("""Spark NLP'yi seviyorum""")
```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|bert_classifier_lex_textclassification_turkish_uncased|
|Compatibility:|Spark NLP 5.1.4+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[document, token]|
|Output Labels:|[class]|
|Language:|tr|
|Size:|414.7 MB|
|Case sensitive:|false|
|Max sentence length:|256|

## References

References

- https://huggingface.co/sfurkan/LexBERT-textclassification-turkish-uncased