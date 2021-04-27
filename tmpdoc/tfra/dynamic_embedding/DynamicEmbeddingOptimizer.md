description: An optimizer wrapper to make any TensorFlow optimizer capable of training

<div itemscope itemtype="http://developers.google.com/ReferenceObject">
<meta itemprop="name" content="tfra.dynamic_embedding.DynamicEmbeddingOptimizer" />
<meta itemprop="path" content="Stable" />
</div>

# tfra.dynamic_embedding.DynamicEmbeddingOptimizer

<!-- Insert buttons and diff -->

<table class="tfo-notebook-buttons tfo-api nocontent" align="left">
<td>
  <a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/dynamic_embedding_optimizer.py#L41-L281">
    <img src="https://www.tensorflow.org/images/GitHub-Mark-32px.png" />
    View source on GitHub
  </a>
</td>
</table>



An optimizer wrapper to make any TensorFlow optimizer capable of training

<section class="expandable">
  <h4 class="showalways">View aliases</h4>
  <p>
<b>Main aliases</b>
<p>`tfra.dynamic_embedding.python.ops.dynamic_embedding_optimizer.DynamicEmbeddingOptimizer`</p>
</p>
</section>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>tfra.dynamic_embedding.DynamicEmbeddingOptimizer(
    self
)
</code></pre>



<!-- Placeholder for "Used in" -->
Dynamic Embeddding Variables.

<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Args</h2></th></tr>

<tr>
<td>
`self`
</td>
<td>
a TensorFlow optimizer.
</td>
</tr>
</table>



#### Example usage:


```python
optimizer = tfra.dynamic_embedding.DynamicEmbeddingOptimizer(
    tf.train.AdamOptimizer(0.001))
```



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Returns</h2></th></tr>
<tr class="alt">
<td colspan="2">
The optimizer itself but has ability to train Dynamic Embedding Variables.
</td>
</tr>

</table>

