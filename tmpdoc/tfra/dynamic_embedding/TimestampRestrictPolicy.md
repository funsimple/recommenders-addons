description: A derived policy to eliminate features in variable follow the

<div itemscope itemtype="http://developers.google.com/ReferenceObject">
<meta itemprop="name" content="tfra.dynamic_embedding.TimestampRestrictPolicy" />
<meta itemprop="path" content="Stable" />
<meta itemprop="property" content="__init__"/>
<meta itemprop="property" content="apply_restriction"/>
<meta itemprop="property" content="apply_update"/>
</div>

# tfra.dynamic_embedding.TimestampRestrictPolicy

<!-- Insert buttons and diff -->

<table class="tfo-notebook-buttons tfo-api nocontent" align="left">
<td>
  <a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/restrict_policies.py#L114-L230">
    <img src="https://www.tensorflow.org/images/GitHub-Mark-32px.png" />
    View source on GitHub
  </a>
</td>
</table>



A derived policy to eliminate features in variable follow the

Inherits From: [`RestrictPolicy`](../../tfra/dynamic_embedding/RestrictPolicy.md)

<section class="expandable">
  <h4 class="showalways">View aliases</h4>
  <p>
<b>Main aliases</b>
<p>`tfra.dynamic_embedding.python.ops.restrict_policies.TimestampRestrictPolicy`</p>
</p>
</section>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>tfra.dynamic_embedding.TimestampRestrictPolicy(
    var
)
</code></pre>



<!-- Placeholder for "Used in" -->
`oldest-out-first` rule.

<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Args</h2></th></tr>

<tr>
<td>
`var`
</td>
<td>
A <a href="../../tfra/dynamic_embedding/Variable.md"><code>dynamic_embedding.Variable</code></a> object to be restricted.
</td>
</tr>
</table>





<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Attributes</h2></th></tr>

<tr>
<td>
`status`
</td>
<td>
Get status variable which save information about properties of features.
</td>
</tr>
</table>



## Methods

<h3 id="apply_restriction"><code>apply_restriction</code></h3>

<a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/restrict_policies.py#L177-L200">View source</a>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>apply_restriction(
    num_reserved, **kwargs
)
</code></pre>

Define the rule to restrict the size of the target variable by eliminating
the oldest k features, and number of `num_reserved` feature will be kept.

<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Args</th></tr>

<tr>
<td>
`num_reserved`
</td>
<td>
int. Number of remained keys after restriction.
</td>
</tr><tr>
<td>
`**kwargs`
</td>
<td>
(Optional) reserved keyword arguments.
trigger: int. The triggered threshold to execute restriction. Default
equals to `num_reserved`.
</td>
</tr>
</table>



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Returns</th></tr>
<tr class="alt">
<td colspan="2">
An operation to restrict the sizes of variable and variables in slots.
</td>
</tr>

</table>



<h3 id="apply_update"><code>apply_update</code></h3>

<a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/restrict_policies.py#L155-L175">View source</a>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>apply_update(
    ids
)
</code></pre>

Define the rule to update the timestamp status. If any feature shows up
in training, then its timestamp will be updated.

<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Args</th></tr>

<tr>
<td>
`ids`
</td>
<td>
A Tensor. Keys appear in training. These keys in status variable
will be updated if needed.
</td>
</tr>
</table>



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Returns</th></tr>
<tr class="alt">
<td colspan="2">
An operation to update timestamp status.
</td>
</tr>

</table>





