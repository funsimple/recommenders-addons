description: A Distributed version of HashTable(reference from lookup_ops.MutableHashTable)

<div itemscope itemtype="http://developers.google.com/ReferenceObject">
<meta itemprop="name" content="tfra.dynamic_embedding.Variable" />
<meta itemprop="path" content="Stable" />
<meta itemprop="property" content="__init__"/>
<meta itemprop="property" content="export"/>
<meta itemprop="property" content="lookup"/>
<meta itemprop="property" content="remove"/>
<meta itemprop="property" content="restrict"/>
<meta itemprop="property" content="size"/>
<meta itemprop="property" content="upsert"/>
</div>

# tfra.dynamic_embedding.Variable

<!-- Insert buttons and diff -->

<table class="tfo-notebook-buttons tfo-api nocontent" align="left">
<td>
  <a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/dynamic_embedding_variable.py#L120-L482">
    <img src="https://www.tensorflow.org/images/GitHub-Mark-32px.png" />
    View source on GitHub
  </a>
</td>
</table>



A Distributed version of HashTable(reference from lookup_ops.MutableHashTable)

<section class="expandable">
  <h4 class="showalways">View aliases</h4>
  <p>
<b>Main aliases</b>
<p>`tfra.dynamic_embedding.python.ops.dynamic_embedding_variable.Variable`</p>
</p>
</section>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>tfra.dynamic_embedding.Variable(
    key_dtype=dtypes.int64, value_dtype=dtypes.float32, dim=1, devices=None, partiti
    oner=tfra.dynamic_embedding.python.ops.dynamic_embedding_variable.default_partit
    ion_fn, shared_name=None, name=&#x27;DynamicEmbedding_Variable&#x27;,
    initializer=None, trainable=True, checkpoint=True, init_size=0,
    restrict_policy=None
)
</code></pre>



<!-- Placeholder for "Used in" -->
It is designed to dynamically store the Sparse Weights(Parameters) of DLRMs.

<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Args</h2></th></tr>

<tr>
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
`name`
</td>
<td>
A name for the operation (optional).
</td>
</tr><tr>
<td>
`initializer`
</td>
<td>
The value to use if a key is missing in the hash table.
which can be a python number, numpy array or `tf.initializer` instances.
If initializer is `None` (the default), `0` will be taken.
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
<tr><th colspan="2"><h2 class="add-link">Attributes</h2></th></tr>

<tr>
<td>
`resource_handle`
</td>
<td>
Returns the resource handle associated with this Resource.
</td>
</tr><tr>
<td>
`restrict_policy`
</td>
<td>

</td>
</tr><tr>
<td>
`tables`
</td>
<td>

</td>
</tr>
</table>



## Methods

<h3 id="export"><code>export</code></h3>

<a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/dynamic_embedding_variable.py#L430-L449">View source</a>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>export(
    name=None
)
</code></pre>

Returns tensors of all keys and values in the table.


<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Args</th></tr>

<tr>
<td>
`name`
</td>
<td>
A name for the operation (optional).
</td>
</tr>
</table>



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Returns</th></tr>
<tr class="alt">
<td colspan="2">
A pair of tensors with the first tensor containing all keys and the
second tensors containing all values in the table.
</td>
</tr>

</table>



<h3 id="lookup"><code>lookup</code></h3>

<a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/dynamic_embedding_variable.py#L395-L428">View source</a>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>lookup(
    keys, name=None
)
</code></pre>

Looks up `keys` in a Variable, outputs the corresponding values.

The `default_value` is used for keys not present in the table.

<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Args</th></tr>

<tr>
<td>
`keys`
</td>
<td>
Keys to look up. Can be a tensor of any shape. Must match the
table's key_dtype.
</td>
</tr><tr>
<td>
`name`
</td>
<td>
A name for the operation (optional).
</td>
</tr>
</table>



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Returns</th></tr>
<tr class="alt">
<td colspan="2">
A tensor containing the values in the same shape as `keys` using the
table's value type.
</td>
</tr>

</table>



<h3 id="remove"><code>remove</code></h3>

<a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/dynamic_embedding_variable.py#L355-L379">View source</a>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>remove(
    keys, name=None
)
</code></pre>

Removes `keys` and its associated values from the variable.

If a key is not present in the table, it is silently ignored.

<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Args</th></tr>

<tr>
<td>
`keys`
</td>
<td>
Keys to remove. Can be a tensor of any shape. Must match the table's
key type.
</td>
</tr><tr>
<td>
`name`
</td>
<td>
A name for the operation (optional).
</td>
</tr>
</table>



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Returns</th></tr>
<tr class="alt">
<td colspan="2">
The created Operation.
</td>
</tr>

</table>



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Raises</th></tr>

<tr>
<td>
`TypeError`
</td>
<td>
when `keys` do not match the table data types.
</td>
</tr>
</table>



<h3 id="restrict"><code>restrict</code></h3>

<a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/dynamic_embedding_variable.py#L335-L353">View source</a>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>restrict(
    num_reserved, **kwargs
)
</code></pre>

Restrict the size of self, also including features reside in commensal
slots, and the policy status. The restriction rule follow the setting
in `restrict_policy`.

<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Args</th></tr>

<tr>
<td>
`num_reserved`
</td>
<td>
int. Number of remaining features after restriction.
</td>
</tr><tr>
<td>
`**kwargs`
</td>
<td>
keyword arguments passing to `restrict_policy.apply_restriction`.
</td>
</tr>
</table>



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Returns</th></tr>
<tr class="alt">
<td colspan="2">
An operation to restrict size of the variable itself. Return None if
the restrict policy is not set.
</td>
</tr>

</table>



<h3 id="size"><code>size</code></h3>

<a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/dynamic_embedding_variable.py#L451-L471">View source</a>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>size(
    index=None, name=None
)
</code></pre>

Compute the number of elements in the index-th table of this Variable.

If index is none, the total size of the Variable wil be return.

<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Args</th></tr>

<tr>
<td>
`index`
</td>
<td>
The index of table (optional)
</td>
</tr><tr>
<td>
`name`
</td>
<td>
A name for the operation (optional).
</td>
</tr>
</table>



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Returns</th></tr>
<tr class="alt">
<td colspan="2">
A scalar tensor containing the number of elements in this Variable.
</td>
</tr>

</table>



<h3 id="upsert"><code>upsert</code></h3>

<a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/dynamic_embedding_variable.py#L301-L333">View source</a>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>upsert(
    keys, values, name=None
)
</code></pre>

Insert or Update `keys` with `values`.

If key exists already, value will be updated.

<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Args</th></tr>

<tr>
<td>
`keys`
</td>
<td>
Keys to insert. Can be a tensor of any shape. Must match the table's
key type.
</td>
</tr><tr>
<td>
`values`
</td>
<td>
Values to be associated with keys. Must be a tensor of the same
shape as `keys` and match the table's value type.
</td>
</tr><tr>
<td>
`name`
</td>
<td>
A name for the operation (optional).
</td>
</tr>
</table>



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Returns</th></tr>
<tr class="alt">
<td colspan="2">
The created Operation.
</td>
</tr>

</table>



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Raises</th></tr>

<tr>
<td>
`TypeError`
</td>
<td>
when `keys` or `values` doesn't match the table data
types.
</td>
</tr>
</table>





