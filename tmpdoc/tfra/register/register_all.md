description: Register TensorFlow Recommenders Addons' objects in TensorFlow global dictionaries.

<div itemscope itemtype="http://developers.google.com/ReferenceObject">
<meta itemprop="name" content="tfra.register.register_all" />
<meta itemprop="path" content="Stable" />
</div>

# tfra.register.register_all

<!-- Insert buttons and diff -->

<table class="tfo-notebook-buttons tfo-api nocontent" align="left">
<td>
  <a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/register.py#L10-L73">
    <img src="https://www.tensorflow.org/images/GitHub-Mark-32px.png" />
    View source on GitHub
  </a>
</td>
</table>



Register TensorFlow Recommenders Addons' objects in TensorFlow global dictionaries.

<section class="expandable">
  <h4 class="showalways">View aliases</h4>
  <p>
<b>Main aliases</b>
<p>`tfra.register_all`</p>
</p>
</section>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>tfra.register.register_all(
    keras_objects: bool = True,
    custom_kernels: bool = True
) -> None
</code></pre>



<!-- Placeholder for "Used in" -->

When loading a Keras model that has a TF Recommenders-Addons' function,
it is needed for this function to be known by the Keras deserialization
process.

There are two ways to do this, either do

```python
tf.keras.models.load_model(
    "my_model.tf",
    custom_objects={"CUCKOO": tfra.dynamic_embedding.CuckooHashTable}
)
```

or you can do:
```python
tfra.register_all()
tf.keras.models.load_model("my_model.tf")
```

If the model contains custom ops (compiled ops) of TensorFlow Addons,
and the graph is loaded with `tf.saved_model.load`, then custom ops need
to be registered before to avoid an error of the type:

```
tensorflow.python.framework.errors_impl.NotFoundError: Op type not registered
'...' in binary running on ... Make sure the Op and Kernel are
registered in the binary running in this process.
```

In this case, the only way to make sure that the ops are registered is to call
this function:

```python
tfra.register_all()
tf.saved_model.load("my_model.tf")
```

Note that you can call this function multiple times in the same process,
it only has an effect the first time. Afterward, it's just a no-op.

<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Args</h2></th></tr>

<tr>
<td>
`keras_objects`
</td>
<td>
boolean, `True` by default. If `True`, register all
Keras objects
with `tf.keras.utils.register_keras_serializable(package="Recommenders-Addons")`
If set to False, doesn't register any Keras objects
of Addons in TensorFlow.
</td>
</tr><tr>
<td>
`custom_kernels`
</td>
<td>
boolean, `True` by default. If `True`, loads all
custom kernels of TensorFlow Recommenders Addons with
`tf.load_op_library("path/to/so/file.so")`. Loading the SO files
register them automatically. If `False` doesn't load and register
the shared objects files. Not that it might be useful to turn it off
if your installation of Recommenders Addons doesn't work well with
custom ops.
</td>
</tr>
</table>



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Returns</h2></th></tr>
<tr class="alt">
<td colspan="2">
None
</td>
</tr>

</table>

