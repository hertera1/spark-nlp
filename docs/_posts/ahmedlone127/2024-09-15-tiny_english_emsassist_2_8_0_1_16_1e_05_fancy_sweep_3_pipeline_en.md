---
layout: model
title: English tiny_english_emsassist_2_8_0_1_16_1e_05_fancy_sweep_3_pipeline pipeline WhisperForCTC from saahith
author: John Snow Labs
name: tiny_english_emsassist_2_8_0_1_16_1e_05_fancy_sweep_3_pipeline
date: 2024-09-15
tags: [en, open_source, pipeline, onnx]
task: Automatic Speech Recognition
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

Pretrained WhisperForCTC, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP.`tiny_english_emsassist_2_8_0_1_16_1e_05_fancy_sweep_3_pipeline` is a English model originally trained by saahith.

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/tiny_english_emsassist_2_8_0_1_16_1e_05_fancy_sweep_3_pipeline_en_5.5.0_3.0_1726431134477.zip){:.button.button-orange.button-orange-trans.arr.button-icon}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/tiny_english_emsassist_2_8_0_1_16_1e_05_fancy_sweep_3_pipeline_en_5.5.0_3.0_1726431134477.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

## How to use



<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}
```python

pipeline = PretrainedPipeline("tiny_english_emsassist_2_8_0_1_16_1e_05_fancy_sweep_3_pipeline", lang = "en")
annotations =  pipeline.transform(df)   

```
```scala

val pipeline = new PretrainedPipeline("tiny_english_emsassist_2_8_0_1_16_1e_05_fancy_sweep_3_pipeline", lang = "en")
val annotations = pipeline.transform(df)

```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|tiny_english_emsassist_2_8_0_1_16_1e_05_fancy_sweep_3_pipeline|
|Type:|pipeline|
|Compatibility:|Spark NLP 5.5.0+|
|License:|Open Source|
|Edition:|Official|
|Language:|en|
|Size:|394.8 MB|

## References

https://huggingface.co/saahith/tiny.en-EMSAssist-2-8-0.1-16-1e-05-fancy-sweep-3

## Included Models

- AudioAssembler
- WhisperForCTC