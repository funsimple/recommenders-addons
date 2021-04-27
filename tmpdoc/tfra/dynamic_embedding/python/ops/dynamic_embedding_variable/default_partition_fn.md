description: The default partition function.

<div itemscope itemtype="http://developers.google.com/ReferenceObject">
<meta itemprop="name" content="tfra.dynamic_embedding.python.ops.dynamic_embedding_variable.default_partition_fn" />
<meta itemprop="path" content="Stable" />
</div>

# tfra.dynamic_embedding.python.ops.dynamic_embedding_variable.default_partition_fn

<!-- Insert buttons and diff -->

<table class="tfo-notebook-buttons tfo-api nocontent" align="left">
<td>
  <a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/dynamic_embedding_variable.py#L79-L100">
    <img src="https://www.tensorflow.org/images/GitHub-Mark-32px.png" />
    View source on GitHub
  </a>
</td>
</table>



The default partition function.

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>tfra.dynamic_embedding.python.ops.dynamic_embedding_variable.default_partition_fn(
    keys, shard_num
)
</code></pre>



<!-- Placeholder for "Used in" -->
  partition keys by "mod" strategy.

  keys: a tensor presents the keys to be partitioned.
  shard_num: the num of partitions
Returns:
  a tensor with same shape as keys with type of `tf.int32`,
    represents the corresponding partition-ids of keys.