description: Gets an Variable object with this name if it exists,

<div itemscope itemtype="http://developers.google.com/ReferenceObject">
<meta itemprop="name" content="tfra.dynamic_embedding.get_variable" />
<meta itemprop="path" content="Stable" />
</div>

# tfra.dynamic_embedding.get_variable

<!-- Insert buttons and diff -->

<table class="tfo-notebook-buttons tfo-api nocontent" align="left">
<td>
  <a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/dynamic_embedding_variable.py#L485-L566">
    <img src="https://www.tensorflow.org/images/GitHub-Mark-32px.png" />
    View source on GitHub
  </a>
</td>
</table>



Gets an `Variable` object with this name if it exists,

<section class="expandable">
  <h4 class="showalways">View aliases</h4>
  <p>
<b>Main aliases</b>
<p>`tfra.dynamic_embedding.python.ops.dynamic_embedding_variable.get_variable`</p>
</p>
</section>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>tfra.dynamic_embedding.get_variable(
    name, key_dtype=dtypes.int64, value_dtype=dtypes.float32, dim=1, devices=None, p
    artitioner=tfra.dynamic_embedding.python.ops.dynamic_embedding_variable.default_
    partition_fn, shared_name=&#x27;get_variable&#x27;, initializer=None,
    trainable=True, checkpoint=True, init_size=0, restrict_policy=None
)
</code></pre>



<!-- Placeholder for "Used in" -->
     or create a new one.

<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Args</h2></th></tr>

<tr>
<td>
`name`
</td>
<td>
A unique name for the `Variable`.
</td>
</tr><tr>
<td>
`key_dtype`
</td>
<td>
the type of the key tensors.
</td>
</tr><tr>
<td>
`value_dtype`
</td>
<td>
the type of the value tensors.
</td>
</tr><tr>
<td>
`dim`
</td>
<td>
the length of the value array for each key.
</td>
</tr><tr>
<td>
`devices`
</td>
<td>
the list of devices holding the tables.
One table will be created on each device.
</td>
</tr><tr>
<td>
`partitioner`
</td>
<td>
partition function of keys,
return the partition index for each key.

Example partition func:
```python
def default_partition_fn(keys, shard_num):
return tf.cast(keys % shard_num, dtype=tf.int32)
```
</td>
</tr><tr>
<td>
`shared_name`
</td>
<td>
No used.
</td>
</tr><tr>
<td>
`initializer`
</td>
<td>
The value to use if a key is missing in the hash table.
which can a python number, numpy array or `tf.initializer` instances.
If initializer is `None` (the default), `0` will be used.
</td>
</tr><tr>
<td>
`trainable`
</td>
<td>
True, will be treated as a trainable Variable, and add to
to the list of variables collected in the graph under the key
`GraphKeys.TRAINABLE_VARIABLES`.
</td>
</tr><tr>
<td>
`checkpoint`
</td>
<td>
if True, the contents of the SparseVariable are
saved to and restored from checkpoints.
If `shared_name` is empty for a checkpointed table,
it is shared using the table node name.
</td>
</tr><tr>
<td>
`init_size`
</td>
<td>
initial size for the Variable and initial size of each hash 
tables will be int(init_size / N), N is the number of the devices.
</td>
</tr><tr>
<td>
`restrict_policy`
</td>
<td>
a restrict policy to specify the rule to restrict the
size of variable. If in training program, the variable is updated by
optimizer, then the sparse slot variables in optimizer are also be
restricted.
</td>
</tr>
</table>



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Returns</h2></th></tr>
<tr class="alt">
<td colspan="2">
A `Variable` object.
</td>
</tr>

</table>

