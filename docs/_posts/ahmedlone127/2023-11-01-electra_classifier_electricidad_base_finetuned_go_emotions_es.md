---
layout: model
title: Spanish ElectraForSequenceClassification Base Cased model (from mrm8488)
author: John Snow Labs
name: electra_classifier_electricidad_base_finetuned_go_emotions
date: 2023-11-01
tags: [es, open_source, electra, sequence_classification, classification, onnx]
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

Pretrained ElectraForSequenceClassification model, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP. `electricidad-base-finetuned-go_emotions-es` is a Spanish model originally trained by `mrm8488`.

## Predicted Entities

`asco`, `deseo`, `remordimiento`, `aprobación`, `gratitud`, `enfado`, `neutral`, `alivio`, `realización`, `molestia`, `dolor`, `sorpresa`, `miedo`, `orgullo`, `decepción`, `admiración`, `amor`, `diversión`, `alegría`, `desaprobación`, `cuidando`, `curiosidad`, `vergüenza`, `excitación`, `optimismo`, `nerviosismo`, `confusión`, `tristeza`

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/electra_classifier_electricidad_base_finetuned_go_emotions_es_5.1.4_3.4_1698805393920.zip){:.button.button-orange.button-orange-trans.arr.button-icon}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/electra_classifier_electricidad_base_finetuned_go_emotions_es_5.1.4_3.4_1698805393920.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

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

seq_classifier = BertForSequenceClassification.pretrained("electra_classifier_electricidad_base_finetuned_go_emotions","es") \
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

val seq_classifier = BertForSequenceClassification.pretrained("electra_classifier_electricidad_base_finetuned_go_emotions","es")
    .setInputCols(Array("document", "token"))
    .setOutputCol("class")

val pipeline = new Pipeline().setStages(Array(documentAssembler, tokenizer, seq_classifier))

val data = Seq("PUT YOUR STRING HERE").toDS.toDF("text")

val result = pipeline.fit(data).transform(data)
```

{:.nlu-block}
```python
import nlu
nlu.load("es.classify.electra.go_emotions.base_finetuned").predict("""PUT YOUR STRING HERE""")
```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|electra_classifier_electricidad_base_finetuned_go_emotions|
|Compatibility:|Spark NLP 5.1.4+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[document, token]|
|Output Labels:|[class]|
|Language:|es|
|Size:|410.6 MB|
|Case sensitive:|true|
|Max sentence length:|256|

## References

References

- https://huggingface.co/mrm8488/electricidad-base-finetuned-go_emotions-es
- https://paperswithcode.com/sota?task=Text+Classification&dataset=go_emotions-es-mt