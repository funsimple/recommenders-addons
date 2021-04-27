description: Shard keys to shard_num partitions

<div itemscope itemtype="http://developers.google.com/ReferenceObject">
<meta itemprop="name" content="tfra.dynamic_embedding.python.ops.dynamic_embedding_variable.make_partition" />
<meta itemprop="path" content="Stable" />
</div>

# tfra.dynamic_embedding.python.ops.dynamic_embedding_variable.make_partition

<!-- Insert buttons and diff -->

<table class="tfo-notebook-buttons tfo-api nocontent" align="left">
<td>
  <a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/dynamic_embedding_variable.py#L45-L68">
    <img src="https://www.tensorflow.org/images/GitHub-Mark-32px.png" />
    View source on GitHub
  </a>
</td>
</table>



Shard keys to shard_num partitions

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>tfra.dynamic_embedding.python.ops.dynamic_embedding_variable.make_partition(
    data, partition_index, shard_num
)
</code></pre>



<!-- Placeholder for "Used in" -->


<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Args</h2></th></tr>

<tr>
<td>
`data`
</td>
<td>
keys or values, usually the IDs of dynamic features.
</td>
</tr><tr>
<td>
`partition_index`
</td>
<td>
partitions index.
</td>
</tr><tr>
<td>
`shard_num`
</td>
<td>
partition number
</td>
</tr>
</table>



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Returns</h2></th></tr>
<tr class="alt">
<td colspan="2">
a pair of tensor: (partition result, partition indices)
</td>
</tr>

</table>

