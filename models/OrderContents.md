<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>
  Class: Spree::OrderContents

    &mdash; Documentation by YARD 0.8.7.6

</title>

  <link rel="stylesheet" href="../css/style.css" type="text/css" charset="utf-8" />

  <link rel="stylesheet" href="../css/common.css" type="text/css" charset="utf-8" />

<script type="text/javascript" charset="utf-8">
  hasFrames = window.top.frames.main ? true : false;
  relpath = '../';
  framesUrl = "../frames.html#!Spree/OrderContents.html";
</script>


  <script type="text/javascript" charset="utf-8" src="../js/jquery.js"></script>

  <script type="text/javascript" charset="utf-8" src="../js/app.js"></script>


  </head>
  <body>
    <div id="header">
      <div id="menu">

    <a href="../_index.html">Index (O)</a> &raquo;
    <span class='title'><span class='object_link'><a href="../Spree.html" title="Spree (module)">Spree</a></span></span>
     &raquo;
    <span class="title">OrderContents</span>


  <div class="noframes"><span class="title">(</span><a href="." target="_top">no frames</a><span class="title">)</span></div>
</div>

      <div id="search">

    <a class="full_list_link" id="class_list_link"
        href="../class_list.html">
      Class List
    </a>

    <a class="full_list_link" id="method_list_link"
        href="../method_list.html">
      Method List
    </a>

    <a class="full_list_link" id="file_list_link"
        href="../file_list.html">
      File List
    </a>

</div>
      <div class="clear"></div>
    </div>

    <iframe id="search_frame"></iframe>

    <div id="content"><h1>Class: Spree::OrderContents



</h1>

<dl class="box">

    <dt class="r1">Inherits:</dt>
    <dd class="r1">
      <span class="inheritName">Object</span>

        <ul class="fullTree">
          <li>Object</li>

            <li class="next">Spree::OrderContents</li>

        </ul>
        <a href="#" class="inheritanceTree">show all</a>

      </dd>









    <dt class="r2 last">Defined in:</dt>
    <dd class="r2 last">order_contents.rb</dd>

</dl>
<div class="clear"></div>





  <h2>Instance Attribute Summary <small>(<a href="#" class="summary_toggle">collapse</a>)</small></h2>
  <ul class="summary">

      <li class="public ">
  <span class="summary_signature">

      <a href="#currency-instance_method" title="#currency (instance method)">- (Object) <strong>currency</strong> </a>



  </span>












    <span class="summary_desc"><div class='inline'>
<p>Returns the value of attribute currency.</p>
</div></span>

</li>


      <li class="public ">
  <span class="summary_signature">

      <a href="#order-instance_method" title="#order (instance method)">- (Object) <strong>order</strong> </a>



  </span>












    <span class="summary_desc"><div class='inline'>
<p>Returns the value of attribute order.</p>
</div></span>

</li>


  </ul>





    <h2>
      Instance Method Summary
      <small>(<a href="#" class="summary_toggle">collapse</a>)</small>
    </h2>

    <ul class="summary">

        <li class="public ">
  <span class="summary_signature">

      <a href="#add-instance_method" title="#add (instance method)">- (Object) <strong>add</strong>(variant, quantity = 1, options = {}) </a>



  </span>









    <span class="summary_desc"><div class='inline'></div></span>

</li>


        <li class="public ">
  <span class="summary_signature">

      <a href="#initialize-instance_method" title="#initialize (instance method)">- (OrderContents) <strong>initialize</strong>(order) </a>



  </span>


    <span class="note title constructor">constructor</span>








    <span class="summary_desc"><div class='inline'>
<p>A new instance of OrderContents.</p>
</div></span>

</li>


        <li class="public ">
  <span class="summary_signature">

      <a href="#remove-instance_method" title="#remove (instance method)">- (Object) <strong>remove</strong>(variant, quantity = 1, options = {}) </a>



  </span>









    <span class="summary_desc"><div class='inline'></div></span>

</li>


        <li class="public ">
  <span class="summary_signature">

      <a href="#update_cart-instance_method" title="#update_cart (instance method)">- (Object) <strong>update_cart</strong>(params) </a>



  </span>









    <span class="summary_desc"><div class='inline'></div></span>

</li>


    </ul>


<div id="constructor_details" class="method_details_list">
  <h2>Constructor Details</h2>

    <div class="method_details first">
  <h3 class="signature first" id="initialize-instance_method">

    - (<tt><span class='object_link'><a href="" title="Spree::OrderContents (class)">OrderContents</a></span></tt>) <strong>initialize</strong>(order)





</h3><div class="docstring">
  <div class="discussion">

<p>Returns a new instance of OrderContents</p>


  </div>
</div>
<div class="tags">


</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


5
6
7</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_contents.rb', line 5</span>

<span class='kw'>def</span> <span class='id identifier rubyid_initialize'>initialize</span><span class='lparen'>(</span><span class='id identifier rubyid_order'>order</span><span class='rparen'>)</span>
  <span class='ivar'>@order</span> <span class='op'>=</span> <span class='id identifier rubyid_order'>order</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>

</div>

  <div id="instance_attr_details" class="attr_details">
    <h2>Instance Attribute Details</h2>


      <span id="currency=-instance_method"></span>
      <div class="method_details first">
  <h3 class="signature first" id="currency-instance_method">

    - (<tt>Object</tt>) <strong>currency</strong>





</h3><div class="docstring">
  <div class="discussion">

<p>Returns the value of attribute currency</p>


  </div>
</div>
<div class="tags">


</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


3
4
5</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_contents.rb', line 3</span>

<span class='kw'>def</span> <span class='id identifier rubyid_currency'>currency</span>
  <span class='ivar'>@currency</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>


      <span id="order=-instance_method"></span>
      <div class="method_details ">
  <h3 class="signature " id="order-instance_method">

    - (<tt>Object</tt>) <strong>order</strong>





</h3><div class="docstring">
  <div class="discussion">

<p>Returns the value of attribute order</p>


  </div>
</div>
<div class="tags">


</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


3
4
5</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_contents.rb', line 3</span>

<span class='kw'>def</span> <span class='id identifier rubyid_order'>order</span>
  <span class='ivar'>@order</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>

  </div>


  <div id="instance_method_details" class="method_details_list">
    <h2>Instance Method Details</h2>


      <div class="method_details first">
  <h3 class="signature first" id="add-instance_method">

    - (<tt>Object</tt>) <strong>add</strong>(variant, quantity = 1, options = {})





</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


9
10
11
12</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_contents.rb', line 9</span>

<span class='kw'>def</span> <span class='id identifier rubyid_add'>add</span><span class='lparen'>(</span><span class='id identifier rubyid_variant'>variant</span><span class='comma'>,</span> <span class='id identifier rubyid_quantity'>quantity</span> <span class='op'>=</span> <span class='int'>1</span><span class='comma'>,</span> <span class='id identifier rubyid_options'>options</span> <span class='op'>=</span> <span class='lbrace'>{</span><span class='rbrace'>}</span><span class='rparen'>)</span>
  <span class='id identifier rubyid_line_item'>line_item</span> <span class='op'>=</span> <span class='id identifier rubyid_add_to_line_item'>add_to_line_item</span><span class='lparen'>(</span><span class='id identifier rubyid_variant'>variant</span><span class='comma'>,</span> <span class='id identifier rubyid_quantity'>quantity</span><span class='comma'>,</span> <span class='id identifier rubyid_options'>options</span><span class='rparen'>)</span>
  <span class='id identifier rubyid_after_add_or_remove'>after_add_or_remove</span><span class='lparen'>(</span><span class='id identifier rubyid_line_item'>line_item</span><span class='comma'>,</span> <span class='id identifier rubyid_options'>options</span><span class='rparen'>)</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>

      <div class="method_details ">
  <h3 class="signature " id="remove-instance_method">

    - (<tt>Object</tt>) <strong>remove</strong>(variant, quantity = 1, options = {})





</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


14
15
16
17</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_contents.rb', line 14</span>

<span class='kw'>def</span> <span class='id identifier rubyid_remove'>remove</span><span class='lparen'>(</span><span class='id identifier rubyid_variant'>variant</span><span class='comma'>,</span> <span class='id identifier rubyid_quantity'>quantity</span> <span class='op'>=</span> <span class='int'>1</span><span class='comma'>,</span> <span class='id identifier rubyid_options'>options</span> <span class='op'>=</span> <span class='lbrace'>{</span><span class='rbrace'>}</span><span class='rparen'>)</span>
  <span class='id identifier rubyid_line_item'>line_item</span> <span class='op'>=</span> <span class='id identifier rubyid_remove_from_line_item'>remove_from_line_item</span><span class='lparen'>(</span><span class='id identifier rubyid_variant'>variant</span><span class='comma'>,</span> <span class='id identifier rubyid_quantity'>quantity</span><span class='comma'>,</span> <span class='id identifier rubyid_options'>options</span><span class='rparen'>)</span>
  <span class='id identifier rubyid_after_add_or_remove'>after_add_or_remove</span><span class='lparen'>(</span><span class='id identifier rubyid_line_item'>line_item</span><span class='comma'>,</span> <span class='id identifier rubyid_options'>options</span><span class='rparen'>)</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>

      <div class="method_details ">
  <h3 class="signature " id="update_cart-instance_method">

    - (<tt>Object</tt>) <strong>update_cart</strong>(params)





</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


19
20
21
22
23
24
25
26
27
28
29
30
31
32
33</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_contents.rb', line 19</span>

<span class='kw'>def</span> <span class='id identifier rubyid_update_cart'>update_cart</span><span class='lparen'>(</span><span class='id identifier rubyid_params'>params</span><span class='rparen'>)</span>
  <span class='kw'>if</span> <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_update_attributes'>update_attributes</span><span class='lparen'>(</span><span class='id identifier rubyid_filter_order_items'>filter_order_items</span><span class='lparen'>(</span><span class='id identifier rubyid_params'>params</span><span class='rparen'>)</span><span class='rparen'>)</span>
    <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_line_items'>line_items</span> <span class='op'>=</span> <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_line_items'>line_items</span><span class='period'>.</span><span class='id identifier rubyid_select'>select</span> <span class='lbrace'>{</span> <span class='op'>|</span><span class='id identifier rubyid_li'>li</span><span class='op'>|</span> <span class='id identifier rubyid_li'>li</span><span class='period'>.</span><span class='id identifier rubyid_quantity'>quantity</span> <span class='op'>&gt;</span> <span class='int'>0</span> <span class='rbrace'>}</span>
    <span class='comment'># Update totals, then check if the order is eligible for any cart promotions.
</span>    <span class='comment'># If we do not update first, then the item total will be wrong and ItemTotal
</span>    <span class='comment'># promotion rules would not be triggered.
</span>    <span class='id identifier rubyid_reload_totals'>reload_totals</span>
    <span class='const'>PromotionHandler</span><span class='op'>::</span><span class='const'>Cart</span><span class='period'>.</span><span class='id identifier rubyid_new'>new</span><span class='lparen'>(</span><span class='id identifier rubyid_order'>order</span><span class='rparen'>)</span><span class='period'>.</span><span class='id identifier rubyid_activate'>activate</span>
    <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_ensure_updated_shipments'>ensure_updated_shipments</span>
    <span class='id identifier rubyid_reload_totals'>reload_totals</span>
    <span class='kw'>true</span>
  <span class='kw'>else</span>
    <span class='kw'>false</span>
  <span class='kw'>end</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>

  </div>

</div>

    <div id="footer">
  Generated on Fri May 15 11:43:05 2015 by
  <a href="http://yardoc.org" title="Yay! A Ruby Documentation Tool" target="_parent">yard</a>
  0.8.7.6 (ruby-2.0.0).
</div>

  </body>
</html>
