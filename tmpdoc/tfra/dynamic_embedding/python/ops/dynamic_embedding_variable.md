description: Dynamic Embedding is designed for Large-scale Sparse Weights Training.

<div itemscope itemtype="http://developers.google.com/ReferenceObject">
<meta itemprop="name" content="tfra.dynamic_embedding.python.ops.dynamic_embedding_variable" />
<meta itemprop="path" content="Stable" />
</div>

# Module: tfra.dynamic_embedding.python.ops.dynamic_embedding_variable

<!-- Insert buttons and diff -->

<table class="tfo-notebook-buttons tfo-api nocontent" align="left">
<td>
  <a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/dynamic_embedding_variable.py">
    <img src="https://www.tensorflow.org/images/GitHub-Mark-32px.png" />
    View source on GitHub
  </a>
</td>
</table>



Dynamic Embedding is designed for Large-scale Sparse Weights Training.

See [Sparse Domain Isolation](https://github.com/tensorflow/community/pull/237)

## Classes

[`class GraphKeys`](../../../../tfra/dynamic_embedding/GraphKeys.md): Extended standard names related to `dynamic_embedding_ops.Variable` to use

[`class Variable`](../../../../tfra/dynamic_embedding/Variable.md): A Distributed version of HashTable(reference from lookup_ops.MutableHashTable)

## Functions

[`default_partition_fn(...)`](../../../../tfra/dynamic_embedding/python/ops/dynamic_embedding_variable/default_partition_fn.md): The default partition function.

[`get_variable(...)`](../../../../tfra/dynamic_embedding/get_variable.md): Gets an `Variable` object with this name if it exists,

[`make_partition(...)`](../../../../tfra/dynamic_embedding/python/ops/dynamic_embedding_variable/make_partition.md): Shard keys to shard_num partitions

[`tf_export(...)`](../../../../tfra/dynamic_embedding/python/ops/dynamic_embedding_ops/tf_export.md): partial(func, *args, **keywords) - new function with partial application

