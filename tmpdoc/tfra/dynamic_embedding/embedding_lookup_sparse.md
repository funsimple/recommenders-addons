description: Provides a dynamic version of embedding_lookup_sparse

<div itemscope itemtype="http://developers.google.com/ReferenceObject">
<meta itemprop="name" content="tfra.dynamic_embedding.embedding_lookup_sparse" />
<meta itemprop="path" content="Stable" />
</div>

# tfra.dynamic_embedding.embedding_lookup_sparse

<!-- Insert buttons and diff -->

<table class="tfo-notebook-buttons tfo-api nocontent" align="left">
<td>
  <a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/dynamic_embedding_ops.py#L557-L730">
    <img src="https://www.tensorflow.org/images/GitHub-Mark-32px.png" />
    View source on GitHub
  </a>
</td>
</table>



Provides a dynamic version of embedding_lookup_sparse

<section class="expandable">
  <h4 class="showalways">View aliases</h4>
  <p>
<b>Main aliases</b>
<p>`tfra.dynamic_embedding.python.ops.dynamic_embedding_ops.embedding_lookup_sparse`</p>
</p>
</section>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>tfra.dynamic_embedding.embedding_lookup_sparse(
    params, sp_ids, sp_weights, partition_strategy=None,
    name=&#x27;embedding_lookup_sparse&#x27;, combiner=&#x27;mean&#x27;,
    max_norm=None, return_trainable=False
)
</code></pre>



<!-- Placeholder for "Used in" -->
  similar with tf.nn.embedding_lookup_sparse.

This op assumes that there is at least one id for each row in the dense tensor
represented by sp_ids (i.e. there are no rows with empty features), and that
all the indices of sp_ids are in canonical row-major order.

It also assumes that all id values lie in the range [0, p0), where p0
is the sum of the size of params along dimension 0.

<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Args</h2></th></tr>

<tr>
<td>
`params`
</td>
<td>
A single <a href="../../tfra/dynamic_embedding/Variable.md"><code>dynamic_embedding.Variable</code></a> instance representing
the complete embedding tensor.
</td>
</tr><tr>
<td>
`sp_ids`
</td>
<td>
N x M `SparseTensor` of int64 ids where N is typically batch size
and M is arbitrary.
</td>
</tr><tr>
<td>
`sp_weights`
</td>
<td>
either a `SparseTensor` of float / double weights, or `None` to
indicate all weights should be taken to be 1. If specified, `sp_weights`
must have exactly the same shape and indices as `sp_ids`.
</td>
</tr><tr>
<td>
`partition_strategy`
</td>
<td>
No used.
</td>
</tr><tr>
<td>
`name`
</td>
<td>
Optional name for the op.
</td>
</tr><tr>
<td>
`combiner`
</td>
<td>
A string specifying the reduction op. Currently "mean", "sqrtn"
and "sum" are supported. "sum" computes the weighted sum of the embedding
results for each row. "mean" is the weighted sum divided by the total
weight. "sqrtn" is the weighted sum divided by the square root of the sum
of the squares of the weights.
</td>
</tr><tr>
<td>
`max_norm`
</td>
<td>
If not `None`, each embedding is clipped if its l2-norm is larger
than this value, before combining.
</td>
</tr><tr>
<td>
`return_trainable`
</td>
<td>
optional, If True, also return TrainableWrapper create by
<a href="../../tfra/dynamic_embedding/embedding_lookup.md"><code>dynamic_embedding.embedding_lookup</code></a>
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
A dense tensor representing the combined embeddings
for the sparse ids. For each row in the dense tensor represented by
`sp_ids`, the op looks up the embeddings for all ids in that row,
multiplies them by the corresponding weight, and combines these embeddings
as specified.

In other words, if

`shape(combined params) = [+infinity, dim]`

and

`shape(sp_ids) = shape(sp_weights) = [d0, d1, ..., dn]`

then

`shape(output) = [d0, dim]`.

For instance, if params dim=20, and sp_ids / sp_weights are

```python
[0, 0]: id 1, weight 2.0
[0, 1]: id 3, weight 0.5
[1, 0]: id 0, weight 1.0
[2, 3]: id 1, weight 3.0
```

with `combiner`="mean", then the output will be a 3x20 matrix where

```python
output[0, :] = (params[1, :] * 2.0 + params[3, :] * 0.5) / (2.0 + 0.5)
output[1, :] = (params[0, :] * 1.0) / 1.0
output[2, :] = (params[1, :] * 3.0) / 3.0
```
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
`TypeError`
</td>
<td>
If `sp_ids` is not a `SparseTensor`, or if `sp_weights` is
neither `None` nor `SparseTensor`.
</td>
</tr><tr>
<td>
`ValueError`
</td>
<td>
If `combiner` is not one of {"mean", "sqrtn", "sum"}.
</td>
</tr>
</table>

