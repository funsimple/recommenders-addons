description: Version of embedding_lookup that avoids duplicate lookups.

<div itemscope itemtype="http://developers.google.com/ReferenceObject">
<meta itemprop="name" content="tfra.dynamic_embedding.embedding_lookup_unique" />
<meta itemprop="path" content="Stable" />
</div>

# tfra.dynamic_embedding.embedding_lookup_unique

<!-- Insert buttons and diff -->

<table class="tfo-notebook-buttons tfo-api nocontent" align="left">
<td>
  <a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/dynamic_embedding_ops.py#L506-L554">
    <img src="https://www.tensorflow.org/images/GitHub-Mark-32px.png" />
    View source on GitHub
  </a>
</td>
</table>



Version of embedding_lookup that avoids duplicate lookups.

<section class="expandable">
  <h4 class="showalways">View aliases</h4>
  <p>
<b>Main aliases</b>
<p>`tfra.dynamic_embedding.python.ops.dynamic_embedding_ops.embedding_lookup_unique`</p>
</p>
</section>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>tfra.dynamic_embedding.embedding_lookup_unique(
    params, ids, partition_strategy=None, name=None, validate_indices=None,
    max_norm=None, return_trainable=False
)
</code></pre>



<!-- Placeholder for "Used in" -->
This can save communication in the case of repeated ids.
Same interface as embedding_lookup.

<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Args</h2></th></tr>

<tr>
<td>
`params`
</td>
<td>
A dynamic_embedding.Variable instance.
</td>
</tr><tr>
<td>
`ids`
</td>
<td>
a tensor with any shape as same dtype of params.key_dtype.
</td>
</tr><tr>
<td>
`partition_strategy`
</td>
<td>
No used, for API compatiblity with `nn.emedding_lookup`.
</td>
</tr><tr>
<td>
`name`
</td>
<td>
A name for the operation (optional).
</td>
</tr><tr>
<td>
`validate_indices`
</td>
<td>
No used, just for compatible with nn.embedding_lookup .
</td>
</tr><tr>
<td>
`max_norm`
</td>
<td>
If not `None`, each embedding is clipped if its l2-norm is larger
than this value.
</td>
</tr><tr>
<td>
`return_trainable`
</td>
<td>
optional, If True, also return TrainableWrapper
</td>
</tr>
</table>



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Returns</h2></th></tr>
<tr class="alt">
<td colspan="2">
A tensor with shape [shape of ids] + [dim],
dim is equal to the value dim of params.
containing the values from the params tensor(s) for keys in ids.
</td>
</tr>
<tr>
<td>
`trainable_wrap`
</td>
<td>
A TrainableWrapper object used to fill the Optimizers `var_list`
Only provided if `return_trainable` is True.
</td>
</tr>
</table>

