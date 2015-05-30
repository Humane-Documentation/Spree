<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>
  Class: Spree::OrderUpdater
  
    &mdash; Documentation by YARD 0.8.7.6
  
</title>

  <link rel="stylesheet" href="../css/style.css" type="text/css" charset="utf-8" />

  <link rel="stylesheet" href="../css/common.css" type="text/css" charset="utf-8" />

<script type="text/javascript" charset="utf-8">
  hasFrames = window.top.frames.main ? true : false;
  relpath = '../';
  framesUrl = "../frames.html#!Spree/OrderUpdater.html";
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
    <span class="title">OrderUpdater</span>
  

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

    <div id="content"><h1>Class: Spree::OrderUpdater
  
  
  
</h1>

<dl class="box">
  
    <dt class="r1">Inherits:</dt>
    <dd class="r1">
      <span class="inheritName">Object</span>
      
        <ul class="fullTree">
          <li>Object</li>
          
            <li class="next">Spree::OrderUpdater</li>
          
        </ul>
        <a href="#" class="inheritanceTree">show all</a>
      
      </dd>
    
  
  
    
  
    
  
  
  
    <dt class="r2 last">Defined in:</dt>
    <dd class="r2 last">order_updater.rb</dd>
  
</dl>
<div class="clear"></div>





  <h2>Instance Attribute Summary <small>(<a href="#" class="summary_toggle">collapse</a>)</small></h2>
  <ul class="summary">
    
      <li class="public ">
  <span class="summary_signature">
    
      <a href="#order-instance_method" title="#order (instance method)">- (Object) <strong>order</strong> </a>
    

    
  </span>
  
  
  
    
      <span class="note title readonly">readonly</span>
    
    
  
  
  
  
  

  
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
    
      <a href="#initialize-instance_method" title="#initialize (instance method)">- (OrderUpdater) <strong>initialize</strong>(order) </a>
    

    
  </span>
  
  
    <span class="note title constructor">constructor</span>
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'>
<p>A new instance of OrderUpdater.</p>
</div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#persist_totals-instance_method" title="#persist_totals (instance method)">- (Object) <strong>persist_totals</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#recalculate_adjustments-instance_method" title="#recalculate_adjustments (instance method)">- (Object) <strong>recalculate_adjustments</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#run_hooks-instance_method" title="#run_hooks (instance method)">- (Object) <strong>run_hooks</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#update-instance_method" title="#update (instance method)">- (Object) <strong>update</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'>
<p>This is a multi-purpose method for processing logic related to changes in
the Order.</p>
</div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#update_adjustment_total-instance_method" title="#update_adjustment_total (instance method)">- (Object) <strong>update_adjustment_total</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#update_item_count-instance_method" title="#update_item_count (instance method)">- (Object) <strong>update_item_count</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#update_item_total-instance_method" title="#update_item_total (instance method)">- (Object) <strong>update_item_total</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#update_order_total-instance_method" title="#update_order_total (instance method)">- (Object) <strong>update_order_total</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#update_payment_state-instance_method" title="#update_payment_state (instance method)">- (Object) <strong>update_payment_state</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'>
<p>Updates the <code>payment_state</code> attribute according to the following
logic:.</p>
</div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#update_payment_total-instance_method" title="#update_payment_total (instance method)">- (Object) <strong>update_payment_total</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#update_shipment_state-instance_method" title="#update_shipment_state (instance method)">- (Object) <strong>update_shipment_state</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'>
<p>Updates the <code>shipment_state</code> attribute according to the
following logic:.</p>
</div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#update_shipment_total-instance_method" title="#update_shipment_total (instance method)">- (Object) <strong>update_shipment_total</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#update_shipments-instance_method" title="#update_shipments (instance method)">- (Object) <strong>update_shipments</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'>
<p>give each of the shipments a chance to update themselves.</p>
</div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#update_totals-instance_method" title="#update_totals (instance method)">- (Object) <strong>update_totals</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'>
<p>Updates the following Order total values:.</p>
</div></span>
  
</li>

      
    </ul>
  

<div id="constructor_details" class="method_details_list">
  <h2>Constructor Details</h2>
  
    <div class="method_details first">
  <h3 class="signature first" id="initialize-instance_method">
  
    - (<tt><span class='object_link'><a href="" title="Spree::OrderUpdater (class)">OrderUpdater</a></span></tt>) <strong>initialize</strong>(order) 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    
<p>Returns a new instance of OrderUpdater</p>


  </div>
</div>
<div class="tags">
  

</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


6
7
8</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_updater.rb', line 6</span>

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
    
      
      <span id=""></span>
      <div class="method_details first">
  <h3 class="signature first" id="order-instance_method">
  
    - (<tt>Object</tt>) <strong>order</strong>  <span class="extras">(readonly)</span>
  

  

  
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
      <pre class="code"><span class="info file"># File 'order_updater.rb', line 3</span>

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
  <h3 class="signature first" id="persist_totals-instance_method">
  
    - (<tt>Object</tt>) <strong>persist_totals</strong> 
  

  

  
</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_updater.rb', line 100</span>

<span class='kw'>def</span> <span class='id identifier rubyid_persist_totals'>persist_totals</span>
  <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_update_columns'>update_columns</span><span class='lparen'>(</span>
      <span class='label'>payment_state:</span>        <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_payment_state'>payment_state</span><span class='comma'>,</span>
      <span class='label'>shipment_state:</span>       <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_shipment_state'>shipment_state</span><span class='comma'>,</span>
      <span class='label'>item_total:</span>           <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_item_total'>item_total</span><span class='comma'>,</span>
      <span class='label'>item_count:</span>           <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_item_count'>item_count</span><span class='comma'>,</span>
      <span class='label'>adjustment_total:</span>     <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_adjustment_total'>adjustment_total</span><span class='comma'>,</span>
      <span class='label'>included_tax_total:</span>   <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_included_tax_total'>included_tax_total</span><span class='comma'>,</span>
      <span class='label'>additional_tax_total:</span> <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_additional_tax_total'>additional_tax_total</span><span class='comma'>,</span>
      <span class='label'>payment_total:</span>        <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_payment_total'>payment_total</span><span class='comma'>,</span>
      <span class='label'>shipment_total:</span>       <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_shipment_total'>shipment_total</span><span class='comma'>,</span>
      <span class='label'>promo_total:</span>          <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_promo_total'>promo_total</span><span class='comma'>,</span>
      <span class='label'>total:</span>                <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_total'>total</span><span class='comma'>,</span>
      <span class='label'>updated_at:</span>           <span class='const'>Time</span><span class='period'>.</span><span class='id identifier rubyid_now'>now</span><span class='comma'>,</span>
  <span class='rparen'>)</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="recalculate_adjustments-instance_method">
  
    - (<tt>Object</tt>) <strong>recalculate_adjustments</strong> 
  

  

  
</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


32
33
34
35
36</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_updater.rb', line 32</span>

<span class='kw'>def</span> <span class='id identifier rubyid_recalculate_adjustments'>recalculate_adjustments</span>
  <span class='id identifier rubyid_all_adjustments'>all_adjustments</span><span class='period'>.</span><span class='id identifier rubyid_includes'>includes</span><span class='lparen'>(</span><span class='symbol'>:adjustable</span><span class='rparen'>)</span><span class='period'>.</span><span class='id identifier rubyid_map'>map</span><span class='lparen'>(</span><span class='op'>&amp;</span><span class='symbol'>:adjustable</span><span class='rparen'>)</span><span class='period'>.</span><span class='id identifier rubyid_uniq'>uniq</span><span class='period'>.</span><span class='id identifier rubyid_each'>each</span> <span class='kw'>do</span> <span class='op'>|</span><span class='id identifier rubyid_adjustable'>adjustable</span><span class='op'>|</span>
    <span class='const'>Adjustable</span><span class='op'>::</span><span class='const'>AdjustmentsUpdater</span><span class='period'>.</span><span class='id identifier rubyid_update'>update</span><span class='lparen'>(</span><span class='id identifier rubyid_adjustable'>adjustable</span><span class='rparen'>)</span>
  <span class='kw'>end</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="run_hooks-instance_method">
  
    - (<tt>Object</tt>) <strong>run_hooks</strong> 
  

  

  
</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


28
29
30</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_updater.rb', line 28</span>

<span class='kw'>def</span> <span class='id identifier rubyid_run_hooks'>run_hooks</span>
  <span class='id identifier rubyid_update_hooks'>update_hooks</span><span class='period'>.</span><span class='id identifier rubyid_each'>each</span> <span class='lbrace'>{</span> <span class='op'>|</span><span class='id identifier rubyid_hook'>hook</span><span class='op'>|</span> <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_send'>send</span> <span class='id identifier rubyid_hook'>hook</span> <span class='rbrace'>}</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="update-instance_method">
  
    - (<tt>Object</tt>) <strong>update</strong> 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    
<p>This is a multi-purpose method for processing logic related to changes in
the Order. It is meant to be called from various observers so that the
Order is aware of changes that affect totals and other values stored in the
Order.</p>

<p>This method should never do anything to the Order that results in a save
call on the object with callbacks (otherwise you will end up in an infinite
recursion as the associations try to save and then in turn try to call
<code>update!</code> again.)</p>


  </div>
</div>
<div class="tags">
  

</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


17
18
19
20
21
22
23
24
25
26</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_updater.rb', line 17</span>

<span class='kw'>def</span> <span class='id identifier rubyid_update'>update</span>
  <span class='id identifier rubyid_update_totals'>update_totals</span>
  <span class='kw'>if</span> <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_completed?'>completed?</span>
    <span class='id identifier rubyid_update_payment_state'>update_payment_state</span>
    <span class='id identifier rubyid_update_shipments'>update_shipments</span>
    <span class='id identifier rubyid_update_shipment_state'>update_shipment_state</span>
  <span class='kw'>end</span>
  <span class='id identifier rubyid_run_hooks'>run_hooks</span>
  <span class='id identifier rubyid_persist_totals'>persist_totals</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="update_adjustment_total-instance_method">
  
    - (<tt>Object</tt>) <strong>update_adjustment_total</strong> 
  

  

  
</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


76
77
78
79
80
81
82
83
84
85
86
87
88
89</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_updater.rb', line 76</span>

<span class='kw'>def</span> <span class='id identifier rubyid_update_adjustment_total'>update_adjustment_total</span>
  <span class='id identifier rubyid_recalculate_adjustments'>recalculate_adjustments</span>
  <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_adjustment_total'>adjustment_total</span>     <span class='op'>=</span> <span class='id identifier rubyid_line_items'>line_items</span><span class='period'>.</span><span class='id identifier rubyid_sum'>sum</span><span class='lparen'>(</span><span class='symbol'>:adjustment_total</span><span class='rparen'>)</span> <span class='op'>+</span>
      <span class='id identifier rubyid_shipments'>shipments</span><span class='period'>.</span><span class='id identifier rubyid_sum'>sum</span><span class='lparen'>(</span><span class='symbol'>:adjustment_total</span><span class='rparen'>)</span> <span class='op'>+</span>
      <span class='id identifier rubyid_adjustments'>adjustments</span><span class='period'>.</span><span class='id identifier rubyid_eligible'>eligible</span><span class='period'>.</span><span class='id identifier rubyid_sum'>sum</span><span class='lparen'>(</span><span class='symbol'>:amount</span><span class='rparen'>)</span>
  <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_included_tax_total'>included_tax_total</span>   <span class='op'>=</span> <span class='id identifier rubyid_line_items'>line_items</span><span class='period'>.</span><span class='id identifier rubyid_sum'>sum</span><span class='lparen'>(</span><span class='symbol'>:included_tax_total</span><span class='rparen'>)</span> <span class='op'>+</span> <span class='id identifier rubyid_shipments'>shipments</span><span class='period'>.</span><span class='id identifier rubyid_sum'>sum</span><span class='lparen'>(</span><span class='symbol'>:included_tax_total</span><span class='rparen'>)</span>
  <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_additional_tax_total'>additional_tax_total</span> <span class='op'>=</span> <span class='id identifier rubyid_line_items'>line_items</span><span class='period'>.</span><span class='id identifier rubyid_sum'>sum</span><span class='lparen'>(</span><span class='symbol'>:additional_tax_total</span><span class='rparen'>)</span> <span class='op'>+</span> <span class='id identifier rubyid_shipments'>shipments</span><span class='period'>.</span><span class='id identifier rubyid_sum'>sum</span><span class='lparen'>(</span><span class='symbol'>:additional_tax_total</span><span class='rparen'>)</span>

  <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_promo_total'>promo_total</span> <span class='op'>=</span> <span class='id identifier rubyid_line_items'>line_items</span><span class='period'>.</span><span class='id identifier rubyid_sum'>sum</span><span class='lparen'>(</span><span class='symbol'>:promo_total</span><span class='rparen'>)</span> <span class='op'>+</span>
      <span class='id identifier rubyid_shipments'>shipments</span><span class='period'>.</span><span class='id identifier rubyid_sum'>sum</span><span class='lparen'>(</span><span class='symbol'>:promo_total</span><span class='rparen'>)</span> <span class='op'>+</span>
      <span class='id identifier rubyid_adjustments'>adjustments</span><span class='period'>.</span><span class='id identifier rubyid_promotion'>promotion</span><span class='period'>.</span><span class='id identifier rubyid_eligible'>eligible</span><span class='period'>.</span><span class='id identifier rubyid_sum'>sum</span><span class='lparen'>(</span><span class='symbol'>:amount</span><span class='rparen'>)</span>

  <span class='id identifier rubyid_update_order_total'>update_order_total</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="update_item_count-instance_method">
  
    - (<tt>Object</tt>) <strong>update_item_count</strong> 
  

  

  
</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


91
92
93</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_updater.rb', line 91</span>

<span class='kw'>def</span> <span class='id identifier rubyid_update_item_count'>update_item_count</span>
  <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_item_count'>item_count</span> <span class='op'>=</span> <span class='id identifier rubyid_quantity'>quantity</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="update_item_total-instance_method">
  
    - (<tt>Object</tt>) <strong>update_item_total</strong> 
  

  

  
</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


95
96
97
98</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_updater.rb', line 95</span>

<span class='kw'>def</span> <span class='id identifier rubyid_update_item_total'>update_item_total</span>
  <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_item_total'>item_total</span> <span class='op'>=</span> <span class='id identifier rubyid_line_items'>line_items</span><span class='period'>.</span><span class='id identifier rubyid_sum'>sum</span><span class='lparen'>(</span><span class='tstring'><span class='tstring_beg'>&#39;</span><span class='tstring_content'>price * quantity</span><span class='tstring_end'>&#39;</span></span><span class='rparen'>)</span>
  <span class='id identifier rubyid_update_order_total'>update_order_total</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="update_order_total-instance_method">
  
    - (<tt>Object</tt>) <strong>update_order_total</strong> 
  

  

  
</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


72
73
74</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_updater.rb', line 72</span>

<span class='kw'>def</span> <span class='id identifier rubyid_update_order_total'>update_order_total</span>
  <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_total'>total</span> <span class='op'>=</span> <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_item_total'>item_total</span> <span class='op'>+</span> <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_shipment_total'>shipment_total</span> <span class='op'>+</span> <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_adjustment_total'>adjustment_total</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="update_payment_state-instance_method">
  
    - (<tt>Object</tt>) <strong>update_payment_state</strong> 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    
<p>Updates the <code>payment_state</code> attribute according to the following
logic:</p>

<p>paid          when <code>payment_total</code> is equal to
<code>total</code> balance_due   when <code>payment_total</code> is less
than <code>total</code> credit_owed   when <code>payment_total</code> is
greater than <code>total</code> failed        when most recent payment is
in the failed state</p>

<p>The <code>payment_state</code> value helps with reporting, etc. since it
provides a quick and easy way to locate Orders needing attention.</p>


  </div>
</div>
<div class="tags">
  

</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


159
160
161
162
163
164
165
166
167
168
169
170
171
172</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_updater.rb', line 159</span>

<span class='kw'>def</span> <span class='id identifier rubyid_update_payment_state'>update_payment_state</span>
  <span class='id identifier rubyid_last_state'>last_state</span> <span class='op'>=</span> <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_payment_state'>payment_state</span>
  <span class='kw'>if</span> <span class='id identifier rubyid_payments'>payments</span><span class='period'>.</span><span class='id identifier rubyid_present?'>present?</span> <span class='op'>&amp;&amp;</span> <span class='id identifier rubyid_payments'>payments</span><span class='period'>.</span><span class='id identifier rubyid_valid'>valid</span><span class='period'>.</span><span class='id identifier rubyid_size'>size</span> <span class='op'>==</span> <span class='int'>0</span>
    <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_payment_state'>payment_state</span> <span class='op'>=</span> <span class='tstring'><span class='tstring_beg'>&#39;</span><span class='tstring_content'>failed</span><span class='tstring_end'>&#39;</span></span>
  <span class='kw'>elsif</span> <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_state'>state</span> <span class='op'>==</span> <span class='tstring'><span class='tstring_beg'>&#39;</span><span class='tstring_content'>canceled</span><span class='tstring_end'>&#39;</span></span> <span class='op'>&amp;&amp;</span> <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_payment_total'>payment_total</span> <span class='op'>==</span> <span class='int'>0</span>
    <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_payment_state'>payment_state</span> <span class='op'>=</span> <span class='tstring'><span class='tstring_beg'>&#39;</span><span class='tstring_content'>void</span><span class='tstring_end'>&#39;</span></span>
  <span class='kw'>else</span>
    <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_payment_state'>payment_state</span> <span class='op'>=</span> <span class='tstring'><span class='tstring_beg'>&#39;</span><span class='tstring_content'>balance_due</span><span class='tstring_end'>&#39;</span></span> <span class='kw'>if</span> <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_outstanding_balance'>outstanding_balance</span> <span class='op'>&gt;</span> <span class='int'>0</span>
    <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_payment_state'>payment_state</span> <span class='op'>=</span> <span class='tstring'><span class='tstring_beg'>&#39;</span><span class='tstring_content'>credit_owed</span><span class='tstring_end'>&#39;</span></span> <span class='kw'>if</span> <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_outstanding_balance'>outstanding_balance</span> <span class='op'>&lt;</span> <span class='int'>0</span>
    <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_payment_state'>payment_state</span> <span class='op'>=</span> <span class='tstring'><span class='tstring_beg'>&#39;</span><span class='tstring_content'>paid</span><span class='tstring_end'>&#39;</span></span> <span class='kw'>if</span> <span class='op'>!</span><span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_outstanding_balance?'>outstanding_balance?</span>
  <span class='kw'>end</span>
  <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_state_changed'>state_changed</span><span class='lparen'>(</span><span class='tstring'><span class='tstring_beg'>&#39;</span><span class='tstring_content'>payment</span><span class='tstring_end'>&#39;</span></span><span class='rparen'>)</span> <span class='kw'>if</span> <span class='id identifier rubyid_last_state'>last_state</span> <span class='op'>!=</span> <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_payment_state'>payment_state</span>
  <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_payment_state'>payment_state</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="update_payment_total-instance_method">
  
    - (<tt>Object</tt>) <strong>update_payment_total</strong> 
  

  

  
</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


63
64
65</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_updater.rb', line 63</span>

<span class='kw'>def</span> <span class='id identifier rubyid_update_payment_total'>update_payment_total</span>
  <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_payment_total'>payment_total</span> <span class='op'>=</span> <span class='id identifier rubyid_payments'>payments</span><span class='period'>.</span><span class='id identifier rubyid_completed'>completed</span><span class='period'>.</span><span class='id identifier rubyid_includes'>includes</span><span class='lparen'>(</span><span class='symbol'>:refunds</span><span class='rparen'>)</span><span class='period'>.</span><span class='id identifier rubyid_inject'>inject</span><span class='lparen'>(</span><span class='int'>0</span><span class='rparen'>)</span> <span class='lbrace'>{</span> <span class='op'>|</span><span class='id identifier rubyid_sum'>sum</span><span class='comma'>,</span> <span class='id identifier rubyid_payment'>payment</span><span class='op'>|</span> <span class='id identifier rubyid_sum'>sum</span> <span class='op'>+</span> <span class='id identifier rubyid_payment'>payment</span><span class='period'>.</span><span class='id identifier rubyid_amount'>amount</span> <span class='op'>-</span> <span class='id identifier rubyid_payment'>payment</span><span class='period'>.</span><span class='id identifier rubyid_refunds'>refunds</span><span class='period'>.</span><span class='id identifier rubyid_sum'>sum</span><span class='lparen'>(</span><span class='symbol'>:amount</span><span class='rparen'>)</span> <span class='rbrace'>}</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="update_shipment_state-instance_method">
  
    - (<tt>Object</tt>) <strong>update_shipment_state</strong> 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    
<p>Updates the <code>shipment_state</code> attribute according to the
following logic:</p>

<p>shipped   when all Shipments are in the “shipped” state partial   when at
least one Shipment has a state of “shipped” and there is another Shipment
with a state other than “shipped”</p>

<pre class="code ruby"><code class="ruby">or there are InventoryUnits associated with the order that have a state of &quot;sold&quot; but are not associated with a Shipment.</code></pre>

<p>ready     when all Shipments are in the “ready” state backorder when there
is backordered inventory associated with an order pending   when all
Shipments are in the “pending” state</p>

<p>The <code>shipment_state</code> value helps with reporting, etc. since it
provides a quick and easy way to locate Orders needing attention.</p>


  </div>
</div>
<div class="tags">
  

</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_updater.rb', line 127</span>

<span class='kw'>def</span> <span class='id identifier rubyid_update_shipment_state'>update_shipment_state</span>
  <span class='kw'>if</span> <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_backordered?'>backordered?</span>
    <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_shipment_state'>shipment_state</span> <span class='op'>=</span> <span class='tstring'><span class='tstring_beg'>&#39;</span><span class='tstring_content'>backorder</span><span class='tstring_end'>&#39;</span></span>
  <span class='kw'>else</span>
    <span class='comment'># get all the shipment states for this order
</span>    <span class='id identifier rubyid_shipment_states'>shipment_states</span> <span class='op'>=</span> <span class='id identifier rubyid_shipments'>shipments</span><span class='period'>.</span><span class='id identifier rubyid_states'>states</span>
    <span class='kw'>if</span> <span class='id identifier rubyid_shipment_states'>shipment_states</span><span class='period'>.</span><span class='id identifier rubyid_size'>size</span> <span class='op'>&gt;</span> <span class='int'>1</span>
      <span class='comment'># multiple shiment states means it&#39;s most likely partially shipped
</span>      <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_shipment_state'>shipment_state</span> <span class='op'>=</span> <span class='tstring'><span class='tstring_beg'>&#39;</span><span class='tstring_content'>partial</span><span class='tstring_end'>&#39;</span></span>
    <span class='kw'>else</span>
      <span class='comment'># will return nil if no shipments are found
</span>      <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_shipment_state'>shipment_state</span> <span class='op'>=</span> <span class='id identifier rubyid_shipment_states'>shipment_states</span><span class='period'>.</span><span class='id identifier rubyid_first'>first</span>
      <span class='comment'># TODO inventory unit states?
</span>      <span class='comment'># if order.shipment_state &amp;&amp; order.inventory_units.where(:shipment_id =&gt; nil).exists?
</span>      <span class='comment'>#   shipments exist but there are unassigned inventory units
</span>      <span class='comment'>#   order.shipment_state = &#39;partial&#39;
</span>      <span class='comment'># end
</span>    <span class='kw'>end</span>
  <span class='kw'>end</span>

  <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_state_changed'>state_changed</span><span class='lparen'>(</span><span class='tstring'><span class='tstring_beg'>&#39;</span><span class='tstring_content'>shipment</span><span class='tstring_end'>&#39;</span></span><span class='rparen'>)</span>
  <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_shipment_state'>shipment_state</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="update_shipment_total-instance_method">
  
    - (<tt>Object</tt>) <strong>update_shipment_total</strong> 
  

  

  
</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


67
68
69
70</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_updater.rb', line 67</span>

<span class='kw'>def</span> <span class='id identifier rubyid_update_shipment_total'>update_shipment_total</span>
  <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_shipment_total'>shipment_total</span> <span class='op'>=</span> <span class='id identifier rubyid_shipments'>shipments</span><span class='period'>.</span><span class='id identifier rubyid_sum'>sum</span><span class='lparen'>(</span><span class='symbol'>:cost</span><span class='rparen'>)</span>
  <span class='id identifier rubyid_update_order_total'>update_order_total</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="update_shipments-instance_method">
  
    - (<tt>Object</tt>) <strong>update_shipments</strong> 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    
<p>give each of the shipments a chance to update themselves</p>


  </div>
</div>
<div class="tags">
  

</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


54
55
56
57
58
59
60
61</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_updater.rb', line 54</span>

<span class='kw'>def</span> <span class='id identifier rubyid_update_shipments'>update_shipments</span>
  <span class='id identifier rubyid_shipments'>shipments</span><span class='period'>.</span><span class='id identifier rubyid_each'>each</span> <span class='kw'>do</span> <span class='op'>|</span><span class='id identifier rubyid_shipment'>shipment</span><span class='op'>|</span>
    <span class='kw'>next</span> <span class='kw'>unless</span> <span class='id identifier rubyid_shipment'>shipment</span><span class='period'>.</span><span class='id identifier rubyid_persisted?'>persisted?</span>
    <span class='id identifier rubyid_shipment'>shipment</span><span class='period'>.</span><span class='id identifier rubyid_update!'>update!</span><span class='lparen'>(</span><span class='id identifier rubyid_order'>order</span><span class='rparen'>)</span>
    <span class='id identifier rubyid_shipment'>shipment</span><span class='period'>.</span><span class='id identifier rubyid_refresh_rates'>refresh_rates</span>
    <span class='id identifier rubyid_shipment'>shipment</span><span class='period'>.</span><span class='id identifier rubyid_update_amounts'>update_amounts</span>
  <span class='kw'>end</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="update_totals-instance_method">
  
    - (<tt>Object</tt>) <strong>update_totals</strong> 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    
<p>Updates the following Order total values:</p>

<p><code>payment_total</code>      The total value of all finalized Payments
(NOTE: non-finalized Payments are excluded) <code>item_total</code>        
The total value of all LineItems <code>adjustment_total</code>   The total
value of all adjustments (promotions, credits, etc.)
<code>promo_total</code>        The total value of all promotion
adjustments <code>total</code>              The so-called “order total.” 
This is equivalent to <code>item_total</code> plus
<code>adjustment_total</code>.</p>


  </div>
</div>
<div class="tags">
  

</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


45
46
47
48
49
50</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_updater.rb', line 45</span>

<span class='kw'>def</span> <span class='id identifier rubyid_update_totals'>update_totals</span>
  <span class='id identifier rubyid_update_payment_total'>update_payment_total</span>
  <span class='id identifier rubyid_update_item_total'>update_item_total</span>
  <span class='id identifier rubyid_update_shipment_total'>update_shipment_total</span>
  <span class='id identifier rubyid_update_adjustment_total'>update_adjustment_total</span>
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