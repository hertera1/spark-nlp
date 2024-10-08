---
layout: model
title: English RobertaForQuestionAnswering (from phiyodr)
author: John Snow Labs
name: roberta_qa_roberta_large_finetuned_squad2
date: 2023-12-22
tags: [en, open_source, question_answering, roberta, onnx]
task: Question Answering
language: en
edition: Spark NLP 5.2.1
spark_version: 3.0
supported: true
engine: onnx
annotator: RoBertaForQuestionAnswering
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained Question Answering model, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP. `roberta-large-finetuned-squad2` is a English model originally trained by `phiyodr`.

## Predicted Entities



{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/roberta_qa_roberta_large_finetuned_squad2_en_5.2.1_3.0_1703264221223.zip){:.button.button-orange.button-orange-trans.arr.button-icon}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/roberta_qa_roberta_large_finetuned_squad2_en_5.2.1_3.0_1703264221223.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

## How to use



<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}
```python
document_assembler = MultiDocumentAssembler() \ 
.setInputCols(["question", "context"]) \
.setOutputCols(["document_question", "document_context"])

spanClassifier = RoBertaForQuestionAnswering.pretrained("roberta_qa_roberta_large_finetuned_squad2","en") \
.setInputCols(["document_question", "document_context"]) \
.setOutputCol("answer") \
.setCaseSensitive(True)

pipeline = Pipeline().setStages([
document_assembler,
spanClassifier
])

example = spark.createDataFrame([["What's my name?", "My name is Clara and I live in Berkeley."]]).toDF("question", "context")

result = pipeline.fit(example).transform(example)
```
```scala
val document = new MultiDocumentAssembler()
.setInputCols("question", "context")
.setOutputCols("document_question", "document_context")

val spanClassifier = RoBertaForQuestionAnswering
.pretrained("roberta_qa_roberta_large_finetuned_squad2","en")
.setInputCols(Array("document_question", "document_context"))
.setOutputCol("answer")
.setCaseSensitive(true)
.setMaxSentenceLength(512)

val pipeline = new Pipeline().setStages(Array(document, spanClassifier))

val example = Seq(
("Where was John Lenon born?", "John Lenon was born in London and lived in Paris. My name is Sarah and I live in London."),
("What's my name?", "My name is Clara and I live in Berkeley."))
.toDF("question", "context")

val result = pipeline.fit(example).transform(example)
```

{:.nlu-block}
```python
import nlu
nlu.load("en.answer_question.squadv2.roberta.large.by_phiyodr").predict("""What's my name?|||"My name is Clara and I live in Berkeley.""")
```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|roberta_qa_roberta_large_finetuned_squad2|
|Compatibility:|Spark NLP 5.2.1+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[question, context]|
|Output Labels:|[answer]|
|Language:|en|
|Size:|1.3 GB|
|Case sensitive:|true|
|Max sentence length:|512|

## References

References

- https://huggingface.co/phiyodr/roberta-large-finetuned-squad2
- https://rajpurkar.github.io/SQuAD-explorer/dataset/dev-v2.0.json
- https://worksheets.codalab.org/rest/bundles/0x6b567e1cf2e041ec80d7098f031c5c9e/contents/blob/
- https://arxiv.org/abs/1907.11692
- https://arxiv.org/abs/1806.03822
- https://rajpurkar.github.io/SQuAD-explorer/