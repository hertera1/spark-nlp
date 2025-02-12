---
layout: model
title: English mdeberta_xlwa_english_italian_ew_tatar_pe_u0_s1_tingredient_p0_5_drop1_mdeberta_e5_dev96_0 DeBertaForQuestionAnswering from pgajo
author: John Snow Labs
name: mdeberta_xlwa_english_italian_ew_tatar_pe_u0_s1_tingredient_p0_5_drop1_mdeberta_e5_dev96_0
date: 2024-09-02
tags: [en, open_source, onnx, question_answering, deberta]
task: Question Answering
language: en
edition: Spark NLP 5.5.0
spark_version: 3.0
supported: true
engine: onnx
annotator: DeBertaForQuestionAnswering
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained DeBertaForQuestionAnswering model, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP.`mdeberta_xlwa_english_italian_ew_tatar_pe_u0_s1_tingredient_p0_5_drop1_mdeberta_e5_dev96_0` is a English model originally trained by pgajo.

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/mdeberta_xlwa_english_italian_ew_tatar_pe_u0_s1_tingredient_p0_5_drop1_mdeberta_e5_dev96_0_en_5.5.0_3.0_1725268660842.zip){:.button.button-orange.button-orange-trans.arr.button-icon}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/mdeberta_xlwa_english_italian_ew_tatar_pe_u0_s1_tingredient_p0_5_drop1_mdeberta_e5_dev96_0_en_5.5.0_3.0_1725268660842.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

## How to use



<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}
```python
             
documentAssembler = MultiDocumentAssembler() \
     .setInputCol(["question", "context"]) \
     .setOutputCol(["document_question", "document_context"])
    
spanClassifier = DeBertaForQuestionAnswering.pretrained("mdeberta_xlwa_english_italian_ew_tatar_pe_u0_s1_tingredient_p0_5_drop1_mdeberta_e5_dev96_0","en") \
     .setInputCols(["document_question","document_context"]) \
     .setOutputCol("answer")

pipeline = Pipeline().setStages([documentAssembler, spanClassifier])
data = spark.createDataFrame([["What framework do I use?","I use spark-nlp."]]).toDF("document_question", "document_context")
pipelineModel = pipeline.fit(data)
pipelineDF = pipelineModel.transform(data)

```
```scala

val documentAssembler = new MultiDocumentAssembler()
    .setInputCol(Array("question", "context")) 
    .setOutputCol(Array("document_question", "document_context"))
    
val spanClassifier = DeBertaForQuestionAnswering.pretrained("mdeberta_xlwa_english_italian_ew_tatar_pe_u0_s1_tingredient_p0_5_drop1_mdeberta_e5_dev96_0", "en")
    .setInputCols(Array("document_question","document_context")) 
    .setOutputCol("answer") 
    
val pipeline = new Pipeline().setStages(Array(documentAssembler, spanClassifier))
val data = Seq("What framework do I use?","I use spark-nlp.").toDS.toDF("document_question", "document_context")
val pipelineModel = pipeline.fit(data)
val pipelineDF = pipelineModel.transform(data)

```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|mdeberta_xlwa_english_italian_ew_tatar_pe_u0_s1_tingredient_p0_5_drop1_mdeberta_e5_dev96_0|
|Compatibility:|Spark NLP 5.5.0+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[document_question, document_context]|
|Output Labels:|[answer]|
|Language:|en|
|Size:|817.8 MB|

## References

https://huggingface.co/pgajo/mdeberta-xlwa-en-it_EW-TT-PE_U0_S1_Tingredient_P0.5_DROP1_mdeberta_E5_DEV96.0