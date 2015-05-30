<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>
  Class: Spree::Exchange
  
    &mdash; Documentation by YARD 0.8.7.6
  
</title>

  <link rel="stylesheet" href="../css/style.css" type="text/css" charset="utf-8" />

  <link rel="stylesheet" href="../css/common.css" type="text/css" charset="utf-8" />

<script type="text/javascript" charset="utf-8">
  hasFrames = window.top.frames.main ? true : false;
  relpath = '../';
  framesUrl = "../frames.html#!Spree/Exchange.html";
</script>


  <script type="text/javascript" charset="utf-8" src="../js/jquery.js"></script>

  <script type="text/javascript" charset="utf-8" src="../js/app.js"></script>


  </head>
  <body>
    <div id="header">
      <div id="menu">
  
    <a href="../_index.html">Index (E)</a> &raquo;
    <span class='title'><span class='object_link'><a href="../Spree.html" title="Spree (module)">Spree</a></span></span>
     &raquo; 
    <span class="title">Exchange</span>
  

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

    <div id="content"><h1>Class: Spree::Exchange
  
  
  
</h1>

<dl class="box">
  
    <dt class="r1">Inherits:</dt>
    <dd class="r1">
      <span class="inheritName">Object</span>
      
        <ul class="fullTree">
          <li>Object</li>
          
            <li class="next">Spree::Exchange</li>
          
        </ul>
        <a href="#" class="inheritanceTree">show all</a>
      
      </dd>
    
  
  
    
  
    
  
  
  
    <dt class="r2 last">Defined in:</dt>
    <dd class="r2 last">exchange.rb</dd>
  
</dl>
<div class="clear"></div>

<h2>Defined Under Namespace</h2>
<p class="children">
  
    
  
    
      <strong class="classes">Classes:</strong> <span class='object_link'><a href="Exchange/UnableToCreateShipments.html" title="Spree::Exchange::UnableToCreateShipments (class)">UnableToCreateShipments</a></span>
    
  
</p>







  
    <h2>
      Class Method Summary
      <small>(<a href="#" class="summary_toggle">collapse</a>)</small>
    </h2>

    <ul class="summary">
      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#model_name-class_method" title="model_name (class method)">+ (Object) <strong>model_name</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#param_key-class_method" title="param_key (class method)">+ (Object) <strong>param_key</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
    </ul>
  
    <h2>
      Instance Method Summary
      <small>(<a href="#" class="summary_toggle">collapse</a>)</small>
    </h2>

    <ul class="summary">
      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#description-instance_method" title="#description (instance method)">- (Object) <strong>description</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#display_amount-instance_method" title="#display_amount (instance method)">- (Object) <strong>display_amount</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#initialize-instance_method" title="#initialize (instance method)">- (Exchange) <strong>initialize</strong>(order, reimbursement_objects) </a>
    

    
  </span>
  
  
    <span class="note title constructor">constructor</span>
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'>
<p>A new instance of Exchange.</p>
</div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#perform%21-instance_method" title="#perform! (instance method)">- (Object) <strong>perform!</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#to_key-instance_method" title="#to_key (instance method)">- (Object) <strong>to_key</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
    </ul>
  

<div id="constructor_details" class="method_details_list">
  <h2>Constructor Details</h2>
  
    <div class="method_details first">
  <h3 class="signature first" id="initialize-instance_method">
  
    - (<tt><span class='object_link'><a href="" title="Spree::Exchange (class)">Exchange</a></span></tt>) <strong>initialize</strong>(order, reimbursement_objects) 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    
<p>Returns a new instance of Exchange</p>


  </div>
</div>
<div class="tags">
  

</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


6
7
8
9</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'exchange.rb', line 6</span>

<span class='kw'>def</span> <span class='id identifier rubyid_initialize'>initialize</span><span class='lparen'>(</span><span class='id identifier rubyid_order'>order</span><span class='comma'>,</span> <span class='id identifier rubyid_reimbursement_objects'>reimbursement_objects</span><span class='rparen'>)</span>
  <span class='ivar'>@order</span>                 <span class='op'>=</span> <span class='id identifier rubyid_order'>order</span>
  <span class='ivar'>@reimbursement_objects</span> <span class='op'>=</span> <span class='id identifier rubyid_reimbursement_objects'>reimbursement_objects</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
  
</div>


  <div id="class_method_details" class="method_details_list">
    <h2>Class Method Details</h2>

    
      <div class="method_details first">
  <h3 class="signature first" id="model_name-class_method">
  
    + (<tt>Object</tt>) <strong>model_name</strong> 
  

  

  
</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


42
43
44</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'exchange.rb', line 42</span>

<span class='kw'>def</span> <span class='kw'>self</span><span class='period'>.</span><span class='id identifier rubyid_model_name'>model_name</span>
  <span class='const'>Spree</span><span class='op'>::</span><span class='const'>Exchange</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="param_key-class_method">
  
    + (<tt>Object</tt>) <strong>param_key</strong> 
  

  

  
</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


38
39
40</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'exchange.rb', line 38</span>

<span class='kw'>def</span> <span class='kw'>self</span><span class='period'>.</span><span class='id identifier rubyid_param_key'>param_key</span>
  <span class='tstring'><span class='tstring_beg'>&quot;</span><span class='tstring_content'>spree_exchange</span><span class='tstring_end'>&quot;</span></span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
  </div>

  <div id="instance_method_details" class="method_details_list">
    <h2>Instance Method Details</h2>

    
      <div class="method_details first">
  <h3 class="signature first" id="description-instance_method">
  
    - (<tt>Object</tt>) <strong>description</strong> 
  

  

  
</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


11
12
13
14
15</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'exchange.rb', line 11</span>

<span class='kw'>def</span> <span class='id identifier rubyid_description'>description</span>
  <span class='ivar'>@reimbursement_objects</span><span class='period'>.</span><span class='id identifier rubyid_map'>map</span> <span class='kw'>do</span> <span class='op'>|</span><span class='id identifier rubyid_reimbursement_object'>reimbursement_object</span><span class='op'>|</span>
    <span class='tstring'><span class='tstring_beg'>&quot;</span><span class='embexpr_beg'>#{</span><span class='id identifier rubyid_reimbursement_object'>reimbursement_object</span><span class='period'>.</span><span class='id identifier rubyid_variant'>variant</span><span class='period'>.</span><span class='id identifier rubyid_options_text'>options_text</span><span class='embexpr_end'>}</span><span class='tstring_content'> =&gt; </span><span class='embexpr_beg'>#{</span><span class='id identifier rubyid_reimbursement_object'>reimbursement_object</span><span class='period'>.</span><span class='id identifier rubyid_exchange_variant'>exchange_variant</span><span class='period'>.</span><span class='id identifier rubyid_options_text'>options_text</span><span class='embexpr_end'>}</span><span class='tstring_end'>&quot;</span></span>
  <span class='kw'>end</span><span class='period'>.</span><span class='id identifier rubyid_join'>join</span><span class='lparen'>(</span><span class='tstring'><span class='tstring_beg'>&quot;</span><span class='tstring_content'> | </span><span class='tstring_end'>&quot;</span></span><span class='rparen'>)</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="display_amount-instance_method">
  
    - (<tt>Object</tt>) <strong>display_amount</strong> 
  

  

  
</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


17
18
19</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'exchange.rb', line 17</span>

<span class='kw'>def</span> <span class='id identifier rubyid_display_amount'>display_amount</span>
  <span class='const'>Spree</span><span class='op'>::</span><span class='const'>Money</span><span class='period'>.</span><span class='id identifier rubyid_new'>new</span> <span class='ivar'>@reimbursement_objects</span><span class='period'>.</span><span class='id identifier rubyid_map'>map</span><span class='lparen'>(</span><span class='op'>&amp;</span><span class='symbol'>:total</span><span class='rparen'>)</span><span class='period'>.</span><span class='id identifier rubyid_sum'>sum</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="perform!-instance_method">
  
    - (<tt>Object</tt>) <strong>perform!</strong> 
  

  

  
</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


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
32</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'exchange.rb', line 21</span>

<span class='kw'>def</span> <span class='id identifier rubyid_perform!'>perform!</span>
  <span class='id identifier rubyid_shipments'>shipments</span> <span class='op'>=</span> <span class='const'>Spree</span><span class='op'>::</span><span class='const'>Stock</span><span class='op'>::</span><span class='const'>Coordinator</span><span class='period'>.</span><span class='id identifier rubyid_new'>new</span><span class='lparen'>(</span><span class='ivar'>@order</span><span class='comma'>,</span> <span class='ivar'>@reimbursement_objects</span><span class='period'>.</span><span class='id identifier rubyid_map'>map</span><span class='lparen'>(</span><span class='op'>&amp;</span><span class='symbol'>:build_exchange_inventory_unit</span><span class='rparen'>)</span><span class='rparen'>)</span><span class='period'>.</span><span class='id identifier rubyid_shipments'>shipments</span>
  <span class='kw'>if</span> <span class='id identifier rubyid_shipments'>shipments</span><span class='period'>.</span><span class='id identifier rubyid_flat_map'>flat_map</span><span class='lparen'>(</span><span class='op'>&amp;</span><span class='symbol'>:inventory_units</span><span class='rparen'>)</span><span class='period'>.</span><span class='id identifier rubyid_size'>size</span> <span class='op'>!=</span> <span class='ivar'>@reimbursement_objects</span><span class='period'>.</span><span class='id identifier rubyid_size'>size</span>
    <span class='id identifier rubyid_raise'>raise</span> <span class='const'>UnableToCreateShipments</span><span class='period'>.</span><span class='id identifier rubyid_new'>new</span><span class='lparen'>(</span><span class='tstring'><span class='tstring_beg'>&quot;</span><span class='tstring_content'>Could not generate shipments for all items. Out of stock?</span><span class='tstring_end'>&quot;</span></span><span class='rparen'>)</span>
  <span class='kw'>end</span>
  <span class='ivar'>@order</span><span class='period'>.</span><span class='id identifier rubyid_shipments'>shipments</span> <span class='op'>+=</span> <span class='id identifier rubyid_shipments'>shipments</span>
  <span class='ivar'>@order</span><span class='period'>.</span><span class='id identifier rubyid_save!'>save!</span>
  <span class='id identifier rubyid_shipments'>shipments</span><span class='period'>.</span><span class='id identifier rubyid_each'>each</span> <span class='kw'>do</span> <span class='op'>|</span><span class='id identifier rubyid_shipment'>shipment</span><span class='op'>|</span>
    <span class='id identifier rubyid_shipment'>shipment</span><span class='period'>.</span><span class='id identifier rubyid_update!'>update!</span><span class='lparen'>(</span><span class='ivar'>@order</span><span class='rparen'>)</span>
    <span class='id identifier rubyid_shipment'>shipment</span><span class='period'>.</span><span class='id identifier rubyid_finalize!'>finalize!</span>
  <span class='kw'>end</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="to_key-instance_method">
  
    - (<tt>Object</tt>) <strong>to_key</strong> 
  

  

  
</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


34
35
36</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'exchange.rb', line 34</span>

<span class='kw'>def</span> <span class='id identifier rubyid_to_key'>to_key</span>
  <span class='kw'>nil</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
  </div>

</div>

    <div id="footer">
  Generated on Fri May 15 11:43:03 2015 by
  <a href="http://yardoc.org" title="Yay! A Ruby Documentation Tool" target="_parent">yard</a>
  0.8.7.6 (ruby-2.0.0).
</div>

  </body>
</html>