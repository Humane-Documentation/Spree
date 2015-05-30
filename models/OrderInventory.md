<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>
  Class: Spree::OrderInventory
  
    &mdash; Documentation by YARD 0.8.7.6
  
</title>

  <link rel="stylesheet" href="../css/style.css" type="text/css" charset="utf-8" />

  <link rel="stylesheet" href="../css/common.css" type="text/css" charset="utf-8" />

<script type="text/javascript" charset="utf-8">
  hasFrames = window.top.frames.main ? true : false;
  relpath = '../';
  framesUrl = "../frames.html#!Spree/OrderInventory.html";
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
    <span class="title">OrderInventory</span>
  

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

    <div id="content"><h1>Class: Spree::OrderInventory
  
  
  
</h1>

<dl class="box">
  
    <dt class="r1">Inherits:</dt>
    <dd class="r1">
      <span class="inheritName">Object</span>
      
        <ul class="fullTree">
          <li>Object</li>
          
            <li class="next">Spree::OrderInventory</li>
          
        </ul>
        <a href="#" class="inheritanceTree">show all</a>
      
      </dd>
    
  
  
    
  
    
  
  
  
    <dt class="r2 last">Defined in:</dt>
    <dd class="r2 last">order_inventory.rb</dd>
  
</dl>
<div class="clear"></div>





  <h2>Instance Attribute Summary <small>(<a href="#" class="summary_toggle">collapse</a>)</small></h2>
  <ul class="summary">
    
      <li class="public ">
  <span class="summary_signature">
    
      <a href="#line_item-instance_method" title="#line_item (instance method)">- (Object) <strong>line_item</strong> </a>
    

    
  </span>
  
  
  
    
    
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'>
<p>Returns the value of attribute line_item.</p>
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

    
      <li class="public ">
  <span class="summary_signature">
    
      <a href="#variant-instance_method" title="#variant (instance method)">- (Object) <strong>variant</strong> </a>
    

    
  </span>
  
  
  
    
    
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'>
<p>Returns the value of attribute variant.</p>
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
    
      <a href="#initialize-instance_method" title="#initialize (instance method)">- (OrderInventory) <strong>initialize</strong>(order, line_item) </a>
    

    
  </span>
  
  
    <span class="note title constructor">constructor</span>
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'>
<p>A new instance of OrderInventory.</p>
</div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#inventory_units-instance_method" title="#inventory_units (instance method)">- (Object) <strong>inventory_units</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#verify-instance_method" title="#verify (instance method)">- (Object) <strong>verify</strong>(shipment = nil) </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'>
<p>Only verify inventory for completed orders (as orders in frontend checkout
have inventory assigned via <code>order.create_proposed_shipment</code>) or
when shipment is explicitly passed.</p>
</div></span>
  
</li>

      
    </ul>
  

<div id="constructor_details" class="method_details_list">
  <h2>Constructor Details</h2>
  
    <div class="method_details first">
  <h3 class="signature first" id="initialize-instance_method">
  
    - (<tt><span class='object_link'><a href="" title="Spree::OrderInventory (class)">OrderInventory</a></span></tt>) <strong>initialize</strong>(order, line_item) 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    
<p>Returns a new instance of OrderInventory</p>


  </div>
</div>
<div class="tags">
  

</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


5
6
7
8
9</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_inventory.rb', line 5</span>

<span class='kw'>def</span> <span class='id identifier rubyid_initialize'>initialize</span><span class='lparen'>(</span><span class='id identifier rubyid_order'>order</span><span class='comma'>,</span> <span class='id identifier rubyid_line_item'>line_item</span><span class='rparen'>)</span>
  <span class='ivar'>@order</span>     <span class='op'>=</span> <span class='id identifier rubyid_order'>order</span>
  <span class='ivar'>@line_item</span> <span class='op'>=</span> <span class='id identifier rubyid_line_item'>line_item</span>
  <span class='ivar'>@variant</span>   <span class='op'>=</span> <span class='id identifier rubyid_line_item'>line_item</span><span class='period'>.</span><span class='id identifier rubyid_variant'>variant</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
  
</div>

  <div id="instance_attr_details" class="attr_details">
    <h2>Instance Attribute Details</h2>
    
      
      <span id="line_item=-instance_method"></span>
      <div class="method_details first">
  <h3 class="signature first" id="line_item-instance_method">
  
    - (<tt>Object</tt>) <strong>line_item</strong> 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    
<p>Returns the value of attribute line_item</p>


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
      <pre class="code"><span class="info file"># File 'order_inventory.rb', line 3</span>

<span class='kw'>def</span> <span class='id identifier rubyid_line_item'>line_item</span>
  <span class='ivar'>@line_item</span>
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
      <pre class="code"><span class="info file"># File 'order_inventory.rb', line 3</span>

<span class='kw'>def</span> <span class='id identifier rubyid_order'>order</span>
  <span class='ivar'>@order</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      
      <span id="variant=-instance_method"></span>
      <div class="method_details ">
  <h3 class="signature " id="variant-instance_method">
  
    - (<tt>Object</tt>) <strong>variant</strong> 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    
<p>Returns the value of attribute variant</p>


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
      <pre class="code"><span class="info file"># File 'order_inventory.rb', line 3</span>

<span class='kw'>def</span> <span class='id identifier rubyid_variant'>variant</span>
  <span class='ivar'>@variant</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
  </div>


  <div id="instance_method_details" class="method_details_list">
    <h2>Instance Method Details</h2>

    
      <div class="method_details first">
  <h3 class="signature first" id="inventory_units-instance_method">
  
    - (<tt>Object</tt>) <strong>inventory_units</strong> 
  

  

  
</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


32
33
34</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_inventory.rb', line 32</span>

<span class='kw'>def</span> <span class='id identifier rubyid_inventory_units'>inventory_units</span>
  <span class='id identifier rubyid_line_item'>line_item</span><span class='period'>.</span><span class='id identifier rubyid_inventory_units'>inventory_units</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="verify-instance_method">
  
    - (<tt>Object</tt>) <strong>verify</strong>(shipment = nil) 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    
<p>Only verify inventory for completed orders (as orders in frontend checkout
have inventory assigned via <code>order.create_proposed_shipment</code>) or
when shipment is explicitly passed</p>

<p>In case shipment is passed the stock location should only unstock or
restock items if the order is completed. That is so because stock items are
always unstocked when the order is completed through
<code>shipment.finalize</code></p>


  </div>
</div>
<div class="tags">
  

</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


18
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
30</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'order_inventory.rb', line 18</span>

<span class='kw'>def</span> <span class='id identifier rubyid_verify'>verify</span><span class='lparen'>(</span><span class='id identifier rubyid_shipment'>shipment</span> <span class='op'>=</span> <span class='kw'>nil</span><span class='rparen'>)</span>
  <span class='kw'>if</span> <span class='id identifier rubyid_order'>order</span><span class='period'>.</span><span class='id identifier rubyid_completed?'>completed?</span> <span class='op'>||</span> <span class='id identifier rubyid_shipment'>shipment</span><span class='period'>.</span><span class='id identifier rubyid_present?'>present?</span>

    <span class='kw'>if</span> <span class='id identifier rubyid_inventory_units'>inventory_units</span><span class='period'>.</span><span class='id identifier rubyid_size'>size</span> <span class='op'>&lt;</span> <span class='id identifier rubyid_line_item'>line_item</span><span class='period'>.</span><span class='id identifier rubyid_quantity'>quantity</span>
      <span class='id identifier rubyid_quantity'>quantity</span> <span class='op'>=</span> <span class='id identifier rubyid_line_item'>line_item</span><span class='period'>.</span><span class='id identifier rubyid_quantity'>quantity</span> <span class='op'>-</span> <span class='id identifier rubyid_inventory_units'>inventory_units</span><span class='period'>.</span><span class='id identifier rubyid_size'>size</span>

      <span class='id identifier rubyid_shipment'>shipment</span> <span class='op'>=</span> <span class='id identifier rubyid_determine_target_shipment'>determine_target_shipment</span> <span class='kw'>unless</span> <span class='id identifier rubyid_shipment'>shipment</span>
      <span class='id identifier rubyid_add_to_shipment'>add_to_shipment</span><span class='lparen'>(</span><span class='id identifier rubyid_shipment'>shipment</span><span class='comma'>,</span> <span class='id identifier rubyid_quantity'>quantity</span><span class='rparen'>)</span>
    <span class='kw'>elsif</span> <span class='id identifier rubyid_inventory_units'>inventory_units</span><span class='period'>.</span><span class='id identifier rubyid_size'>size</span> <span class='op'>&gt;</span> <span class='id identifier rubyid_line_item'>line_item</span><span class='period'>.</span><span class='id identifier rubyid_quantity'>quantity</span>
      <span class='id identifier rubyid_remove'>remove</span><span class='lparen'>(</span><span class='id identifier rubyid_inventory_units'>inventory_units</span><span class='comma'>,</span> <span class='id identifier rubyid_shipment'>shipment</span><span class='rparen'>)</span>
    <span class='kw'>end</span>
  <span class='kw'>end</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
  </div>

</div>

    <div id="footer">
  Generated on Fri May 15 11:43:06 2015 by
  <a href="http://yardoc.org" title="Yay! A Ruby Documentation Tool" target="_parent">yard</a>
  0.8.7.6 (ruby-2.0.0).
</div>

  </body>
</html>