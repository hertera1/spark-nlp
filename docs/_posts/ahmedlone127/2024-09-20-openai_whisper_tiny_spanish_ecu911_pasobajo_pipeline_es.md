---
layout: model
title: Castilian, Spanish openai_whisper_tiny_spanish_ecu911_pasobajo_pipeline pipeline WhisperForCTC from DanielMarquez
author: John Snow Labs
name: openai_whisper_tiny_spanish_ecu911_pasobajo_pipeline
date: 2024-09-20
tags: [es, open_source, pipeline, onnx]
task: Automatic Speech Recognition
language: es
edition: Spark NLP 5.5.0
spark_version: 3.0
supported: true
annotator: PipelineModel
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained WhisperForCTC, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP.`openai_whisper_tiny_spanish_ecu911_pasobajo_pipeline` is a Castilian, Spanish model originally trained by DanielMarquez.

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/openai_whisper_tiny_spanish_ecu911_pasobajo_pipeline_es_5.5.0_3.0_1726814121844.zip){:.button.button-orange.button-orange-trans.arr.button-icon}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/openai_whisper_tiny_spanish_ecu911_pasobajo_pipeline_es_5.5.0_3.0_1726814121844.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

## How to use



<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}
```python

pipeline = PretrainedPipeline("openai_whisper_tiny_spanish_ecu911_pasobajo_pipeline", lang = "es")
annotations =  pipeline.transform(df)   

```
```scala

val pipeline = new PretrainedPipeline("openai_whisper_tiny_spanish_ecu911_pasobajo_pipeline", lang = "es")
val annotations = pipeline.transform(df)

```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|openai_whisper_tiny_spanish_ecu911_pasobajo_pipeline|
|Type:|pipeline|
|Compatibility:|Spark NLP 5.5.0+|
|License:|Open Source|
|Edition:|Official|
|Language:|es|
|Size:|379.7 MB|

## References

https://huggingface.co/DanielMarquez/openai-whisper-tiny-es_ecu911-PasoBajo

## Included Models

- AudioAssembler
- WhisperForCTC