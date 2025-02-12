---
layout: model
title: English 011_microsoft_deberta_v3_base_finetuned_yahoo_8000_2000_pipeline pipeline DeBertaForSequenceClassification from diogopaes10
author: John Snow Labs
name: 011_microsoft_deberta_v3_base_finetuned_yahoo_8000_2000_pipeline
date: 2024-09-11
tags: [en, open_source, pipeline, onnx]
task: Text Classification
language: en
edition: Spark NLP 5.5.0
spark_version: 3.0
supported: true
annotator: PipelineModel
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained DeBertaForSequenceClassification, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP.`011_microsoft_deberta_v3_base_finetuned_yahoo_8000_2000_pipeline` is a English model originally trained by diogopaes10.

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/011_microsoft_deberta_v3_base_finetuned_yahoo_8000_2000_pipeline_en_5.5.0_3.0_1726030322882.zip){:.button.button-orange.button-orange-trans.arr.button-icon}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/011_microsoft_deberta_v3_base_finetuned_yahoo_8000_2000_pipeline_en_5.5.0_3.0_1726030322882.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

## How to use



<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}
```python

pipeline = PretrainedPipeline("011_microsoft_deberta_v3_base_finetuned_yahoo_8000_2000_pipeline", lang = "en")
annotations =  pipeline.transform(df)   

```
```scala

val pipeline = new PretrainedPipeline("011_microsoft_deberta_v3_base_finetuned_yahoo_8000_2000_pipeline", lang = "en")
val annotations = pipeline.transform(df)

```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|011_microsoft_deberta_v3_base_finetuned_yahoo_8000_2000_pipeline|
|Type:|pipeline|
|Compatibility:|Spark NLP 5.5.0+|
|License:|Open Source|
|Edition:|Official|
|Language:|en|
|Size:|618.4 MB|

## References

https://huggingface.co/diogopaes10/011-microsoft-deberta-v3-base-finetuned-yahoo-8000_2000

## Included Models

- DocumentAssembler
- TokenizerModel
- DeBertaForSequenceClassification