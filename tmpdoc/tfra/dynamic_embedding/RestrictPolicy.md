description: Base class of restrict policies. Never use this class directly, but

<div itemscope itemtype="http://developers.google.com/ReferenceObject">
<meta itemprop="name" content="tfra.dynamic_embedding.RestrictPolicy" />
<meta itemprop="path" content="Stable" />
<meta itemprop="property" content="__init__"/>
<meta itemprop="property" content="apply_restriction"/>
<meta itemprop="property" content="apply_update"/>
</div>

# tfra.dynamic_embedding.RestrictPolicy

<!-- Insert buttons and diff -->

<table class="tfo-notebook-buttons tfo-api nocontent" align="left">
<td>
  <a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/restrict_policies.py#L32-L111">
    <img src="https://www.tensorflow.org/images/GitHub-Mark-32px.png" />
    View source on GitHub
  </a>
</td>
</table>



Base class of restrict policies. Never use this class directly, but

<section class="expandable">
  <h4 class="showalways">View aliases</h4>
  <p>
<b>Main aliases</b>
<p>`tfra.dynamic_embedding.python.ops.restrict_policies.RestrictPolicy`</p>
</p>
</section>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>tfra.dynamic_embedding.RestrictPolicy(
    var
)
</code></pre>



<!-- Placeholder for "Used in" -->
instead of of its derived class.

This class defines the rules for tracking and restricting the size of the
<a href="../../tfra/dynamic_embedding/Variable.md"><code>dynamic_embedding.Variable</code></a>. If the variable joins training via stateful
optimizer, the policy also manage the slots of the optimizer. It could own
a status to keep tracking the state of affairs of the features presented
in sparse <a href="../../tfra/dynamic_embedding/Variable.md"><code>dynamic_embedding.Variable</code></a>.

`RestrictPolicy` requires a set of methods to be override, in its derived
policies: `apply_update`, `apply_restriction`, `status`.

* apply_update: keep tracking on the status of the sparse variable,
    specifically the attributes of each key in sparse variable.
* apply_restriction: eliminate the features which are not legitimate.

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

<a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/restrict_policies.py#L75-L89">View source</a>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>apply_restriction(
    num_reserved, **kwargs
)
</code></pre>

Define the rule to restrict the size of the target variable. There are
three kinds of variables are token into consideration: variable, status
variable, and variables in slots. Number of `num_reserved` features will
be kept in variable.

<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Args</th></tr>

<tr>
<td>
`num_reserved`
</td>
<td>
number of remained keys after restriction.
</td>
</tr><tr>
<td>
`**kwargs`
</td>
<td>
(Optional) reserved keyword arguments.
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

<a target="_blank" href="https://github.com/tensorflow/recommenders-addons/tree/master/tensorflow_recommenders_addons/dynamic_embedding/python/ops/restrict_policies.py#L61-L73">View source</a>

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>apply_update(
    ids
)
</code></pre>

Define the rule to update status, with tracking the
changes in variable and slots.

<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Args</th></tr>

<tr>
<td>
`ids`
</td>
<td>
A Tensor. Keys appear in training. These keys in status
variable will be updated if needed.
</td>
</tr>
</table>



<!-- Tabular view -->
 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2">Returns</th></tr>
<tr class="alt">
<td colspan="2">
An operation to update status.
</td>
</tr>

</table>





