---
layout: model
title: English xtremedistil_l6_h384_uncased_finetuned_wikitext103 BertEmbeddings from saghar
author: John Snow Labs
name: xtremedistil_l6_h384_uncased_finetuned_wikitext103
date: 2023-09-13
tags: [bert, en, open_source, fill_mask, onnx]
task: Embeddings
language: en
edition: Spark NLP 5.1.1
spark_version: 3.0
supported: true
engine: onnx
annotator: BertEmbeddings
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained BertEmbeddings  model, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP.`xtremedistil_l6_h384_uncased_finetuned_wikitext103` is a English model originally trained by saghar.

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/xtremedistil_l6_h384_uncased_finetuned_wikitext103_en_5.1.1_3.0_1694616303708.zip){:.button.button-orange.button-orange-trans.arr.button-icon}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/xtremedistil_l6_h384_uncased_finetuned_wikitext103_en_5.1.1_3.0_1694616303708.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

## How to use



<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}
```python


document_assembler = DocumentAssembler() \
    .setInputCol("text") \
    .setOutputCol("documents")
    
    
embeddings =BertEmbeddings.pretrained("xtremedistil_l6_h384_uncased_finetuned_wikitext103","en") \
            .setInputCols(["documents","token"]) \
            .setOutputCol("embeddings")

pipeline = Pipeline().setStages([document_assembler, embeddings])

pipelineModel = pipeline.fit(data)

pipelineDF = pipelineModel.transform(data)

```
```scala


val document_assembler = new DocumentAssembler()
    .setInputCol("text") 
    .setOutputCol("embeddings")
    
val embeddings = BertEmbeddings 
    .pretrained("xtremedistil_l6_h384_uncased_finetuned_wikitext103", "en")
    .setInputCols(Array("documents","token")) 
    .setOutputCol("embeddings") 

val pipeline = new Pipeline().setStages(Array(document_assembler, embeddings))

val pipelineModel = pipeline.fit(data)

val pipelineDF = pipelineModel.transform(data)


```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|xtremedistil_l6_h384_uncased_finetuned_wikitext103|
|Compatibility:|Spark NLP 5.1.1+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[documents, token]|
|Output Labels:|[embeddings]|
|Language:|en|
|Size:|83.6 MB|

## References

https://huggingface.co/saghar/xtremedistil-l6-h384-uncased-finetuned-wikitext103