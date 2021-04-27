description: The global config of model modes.

<div itemscope itemtype="http://developers.google.com/ReferenceObject">
<meta itemprop="name" content="tfra.dynamic_embedding.ModelMode" />
<meta itemprop="path" content="Stable" />
<meta itemprop="property" content="CURRENT_SETTING"/>
<meta itemprop="property" content="INFERENCE"/>
<meta itemprop="property" content="TRAIN"/>
</div>

# tfra.dynamic_embedding.ModelMode

<!-- Insert buttons and diff -->

<table class="tfo-notebook-buttons tfo-api nocontent" align="left">
<td>
  <a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/dynamic_embedding_ops.py#L886-L908">
    <img src="https://www.tensorflow.org/images/GitHub-Mark-32px.png" />
    View source on GitHub
  </a>
</td>
</table>



The global config of model modes.

<section class="expandable">
  <h4 class="showalways">View aliases</h4>
  <p>
<b>Main aliases</b>
<p>`tfra.dynamic_embedding.python.ops.dynamic_embedding_ops.ModelMode`</p>
</p>
</section>

<!-- Placeholder for "Used in" -->

  <a href="../../tfra/dynamic_embedding/TrainableWrapper.md#read_value"><code>TrainableWrapper.read_value</code></a> is not thread-safe that causes threads
  competition and Out-Of-Bound exception in concurrent serving scenario.

  To resolve this, we define the `ModelMode` APIs to instruct
  the `TrainableWrapper` to build a different thread-safe sub-graph
  for 'TrainableWrapper.read_value' on inference mode.

  **NOTE** These APIs should be called before any graph are built.

The following standard modes are defined:

* `TRAIN`: training/fitting mode.
* `INFERENCE`: prediction/inference mode.



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Class Variables</h2></th></tr>

<tr>
<td>
CURRENT_SETTING<a id="CURRENT_SETTING"></a>
</td>
<td>
`'train'`
</td>
</tr><tr>
<td>
INFERENCE<a id="INFERENCE"></a>
</td>
<td>
`'inference'`
</td>
</tr><tr>
<td>
TRAIN<a id="TRAIN"></a>
</td>
<td>
`'train'`
</td>
</tr>
</table>

