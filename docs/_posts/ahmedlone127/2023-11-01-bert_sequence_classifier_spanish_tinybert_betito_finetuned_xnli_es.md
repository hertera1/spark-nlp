---
layout: model
title: Spanish BertForSequenceClassification Tiny Cased model (from mrm8488)
author: John Snow Labs
name: bert_sequence_classifier_spanish_tinybert_betito_finetuned_xnli
date: 2023-11-01
tags: [es, open_source, bert, sequence_classification, onnx]
task: Text Classification
language: es
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

Pretrained BertForSequenceClassification model, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP. `spanish-TinyBERT-betito-finetuned-xnli-es` is a Spanish model originally trained by `mrm8488`.

## Predicted Entities



{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/bert_sequence_classifier_spanish_tinybert_betito_finetuned_xnli_es_5.1.4_3.4_1698799486383.zip){:.button.button-orange.button-orange-trans.arr.button-icon}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/bert_sequence_classifier_spanish_tinybert_betito_finetuned_xnli_es_5.1.4_3.4_1698799486383.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

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

classifier = BertForSequenceClassification.pretrained("bert_sequence_classifier_spanish_tinybert_betito_finetuned_xnli","es") \
    .setInputCols(["document", "token"]) \
    .setOutputCol("class")

pipeline = Pipeline(stages=[documentAssembler, tokenizer, classifier])

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

val classifer = BertForSequenceClassification.pretrained("bert_sequence_classifier_spanish_tinybert_betito_finetuned_xnli","es")
    .setInputCols(Array("document", "token"))
    .setOutputCol("class")

val pipeline = new Pipeline().setStages(Array(documentAssembler, tokenizer, classifier))

val data = Seq("PUT YOUR STRING HERE").toDS.toDF("text")

val result = pipeline.fit(data).transform(data)
```

{:.nlu-block}
```python
import nlu
nlu.load("es.classify.bert.xnli.tiny_finetuned").predict("""PUT YOUR STRING HERE""")
```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|bert_sequence_classifier_spanish_tinybert_betito_finetuned_xnli|
|Compatibility:|Spark NLP 5.1.4+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[document, token]|
|Output Labels:|[class]|
|Language:|es|
|Size:|54.7 MB|
|Case sensitive:|true|
|Max sentence length:|256|

## References

References

- https://huggingface.co/mrm8488/spanish-TinyBERT-betito-finetuned-xnli-es