description: Provides a dynamic version of tf.nn.safe_embedding_lookup_sparse.

<div itemscope itemtype="http://developers.google.com/ReferenceObject">
<meta itemprop="name" content="tfra.dynamic_embedding.safe_embedding_lookup_sparse" />
<meta itemprop="path" content="Stable" />
</div>

# tfra.dynamic_embedding.safe_embedding_lookup_sparse

<!-- Insert buttons and diff -->

<table class="tfo-notebook-buttons tfo-api nocontent" align="left">
<td>
  <a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/dynamic_embedding_ops.py#L733-L874">
    <img src="https://www.tensorflow.org/images/GitHub-Mark-32px.png" />
    View source on GitHub
  </a>
</td>
</table>



Provides a dynamic version of `tf.nn.safe_embedding_lookup_sparse`.

<section class="expandable">
  <h4 class="showalways">View aliases</h4>
  <p>
<b>Main aliases</b>
<p>`tfra.dynamic_embedding.python.ops.dynamic_embedding_ops.safe_embedding_lookup_sparse`</p>
</p>
</section>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>tfra.dynamic_embedding.safe_embedding_lookup_sparse(
    embedding_weights, sparse_ids, sparse_weights=None, combiner=&#x27;mean&#x27;,
    default_id=None, name=&#x27;safe_embedding_lookup_sparse&#x27;,
    partition_strategy=None, max_norm=None, return_trainable=False
)
</code></pre>



<!-- Placeholder for "Used in" -->

Lookup embedding results, accounting for empty features and invalid weights.

Any IDs will be treated as valid include non-positive IDs.
Invalid weights (<= 0) are pruned from input weights, as well as any IDs
with non-positive weight. For an entry with no features, the embedding vector
for `default_id` is returned, or the 0-vector if `default_id` is not supplied.

The ids and weights may be multi-dimensional. Embeddings are always aggregated
along the last dimension.

<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Args</h2></th></tr>

<tr>
<td>
`embedding_weights`
</td>
<td>
A single <a href="../../tfra/dynamic_embedding/Variable.md"><code>dynamic_embedding.Variable</code></a> instance
representing the complete embedding tensor.
</td>
</tr><tr>
<td>
`sparse_ids`
</td>
<td>
`SparseTensor` of shape `[d_0, d_1, ..., d_n]` containing the
ids. `d_0` is typically batch size.
</td>
</tr><tr>
<td>
`sparse_weights`
</td>
<td>
`SparseTensor` of same shape as `sparse_ids`, containing
float weights corresponding to `sparse_ids`, or `None` if all weights are
be assumed to be 1.0.
</td>
</tr><tr>
<td>
`combiner`
</td>
<td>
A string specifying how to combine embedding results for each
entry. Currently "mean", "sqrtn" and "sum" are supported, with "mean" the
default.
</td>
</tr><tr>
<td>
`default_id`
</td>
<td>
The id to use for an entry with no features.
</td>
</tr><tr>
<td>
`name`
</td>
<td>
A name for this operation (optional).
</td>
</tr><tr>
<td>
`partition_strategy`
</td>
<td>
A string specifying the partitioning strategy. Currently
`"div"` and `"mod"` are supported. Default is `"div"`.
</td>
</tr><tr>
<td>
`max_norm`
</td>
<td>
If not `None`, all embeddings are l2-normalized to max_norm before
combining.
</td>
</tr>
</table>



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Returns</h2></th></tr>

<tr>
<td>
`combined_embeddings`
</td>
<td>
A dense `Tensor` of shape `[d_0, d_1, ..., d_{n-1}, e_1, ..., e_m]`.
</td>
</tr><tr>
<td>
`trainable_wrap`
</td>
<td>
A TrainableWrapper object used to fill the Optimizers `var_list`
Only provided if `return_trainable` is True.
</td>
</tr>
</table>



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Raises</h2></th></tr>

<tr>
<td>
`ValueError`
</td>
<td>
if `embedding_weights` is empty.
</td>
</tr>
</table>

