<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>
  Class: Spree::ShippingCalculator
  
    &mdash; Documentation by YARD 0.8.7.6
  
</title>

  <link rel="stylesheet" href="../css/style.css" type="text/css" charset="utf-8" />

  <link rel="stylesheet" href="../css/common.css" type="text/css" charset="utf-8" />

<script type="text/javascript" charset="utf-8">
  hasFrames = window.top.frames.main ? true : false;
  relpath = '../';
  framesUrl = "../frames.html#!Spree/ShippingCalculator.html";
</script>


  <script type="text/javascript" charset="utf-8" src="../js/jquery.js"></script>

  <script type="text/javascript" charset="utf-8" src="../js/app.js"></script>


  </head>
  <body>
    <div id="header">
      <div id="menu">
  
    <a href="../_index.html">Index (S)</a> &raquo;
    <span class='title'><span class='object_link'><a href="../Spree.html" title="Spree (module)">Spree</a></span></span>
     &raquo; 
    <span class="title">ShippingCalculator</span>
  

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

    <div id="content"><h1>Class: Spree::ShippingCalculator
  
  
  
</h1>

<dl class="box">
  
    <dt class="r1">Inherits:</dt>
    <dd class="r1">
      <span class="inheritName"><span class='object_link'><a href="Calculator.html" title="Spree::Calculator (class)">Calculator</a></span></span>
      
        <ul class="fullTree">
          <li>Object</li>
          
            <li class="next">ActiveRecord::Base</li>
          
            <li class="next"><span class='object_link'><a href="Base.html" title="Spree::Base (class)">Base</a></span></li>
          
            <li class="next"><span class='object_link'><a href="Calculator.html" title="Spree::Calculator (class)">Calculator</a></span></li>
          
            <li class="next">Spree::ShippingCalculator</li>
          
        </ul>
        <a href="#" class="inheritanceTree">show all</a>
      
      </dd>
    
  
  
    
  
    
  
  
  
    <dt class="r2 last">Defined in:</dt>
    <dd class="r2 last">shipping_calculator.rb</dd>
  
</dl>
<div class="clear"></div>

<div id="subclasses">
  <h2>Direct Known Subclasses</h2>
  <p class="children"><span class='object_link'><a href="Calculator/Shipping/FlatPercentItemTotal.html" title="Spree::Calculator::Shipping::FlatPercentItemTotal (class)">Calculator::Shipping::FlatPercentItemTotal</a></span>, <span class='object_link'><a href="Calculator/Shipping/FlatRate.html" title="Spree::Calculator::Shipping::FlatRate (class)">Calculator::Shipping::FlatRate</a></span>, <span class='object_link'><a href="Calculator/Shipping/FlexiRate.html" title="Spree::Calculator::Shipping::FlexiRate (class)">Calculator::Shipping::FlexiRate</a></span>, <span class='object_link'><a href="Calculator/Shipping/PerItem.html" title="Spree::Calculator::Shipping::PerItem (class)">Calculator::Shipping::PerItem</a></span>, <span class='object_link'><a href="Calculator/Shipping/PriceSack.html" title="Spree::Calculator::Shipping::PriceSack (class)">Calculator::Shipping::PriceSack</a></span></p>
</div>







  
    <h2>
      Instance Method Summary
      <small>(<a href="#" class="summary_toggle">collapse</a>)</small>
    </h2>

    <ul class="summary">
      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#available%3F-instance_method" title="#available? (instance method)">- (Boolean) <strong>available?</strong>(package) </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#compute_package-instance_method" title="#compute_package (instance method)">- (Object) <strong>compute_package</strong>(package) </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#compute_shipment-instance_method" title="#compute_shipment (instance method)">- (Object) <strong>compute_shipment</strong>(shipment) </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
    </ul>
  


  
  
  
  
  
  
  
  
  <h3 class="inherited">Methods inherited from <span class='object_link'><a href="Calculator.html" title="Spree::Calculator (class)">Calculator</a></span></h3>
  <p class="inherited"><span class='object_link'><a href="Calculator.html#calculators-class_method" title="Spree::Calculator.calculators (method)">calculators</a></span>, <span class='object_link'><a href="Calculator.html#compute-instance_method" title="Spree::Calculator#compute (method)">#compute</a></span>, <span class='object_link'><a href="Calculator.html#description-instance_method" title="Spree::Calculator#description (method)">#description</a></span>, <span class='object_link'><a href="Calculator.html#description-class_method" title="Spree::Calculator.description (method)">description</a></span>, <span class='object_link'><a href="Calculator.html#register-class_method" title="Spree::Calculator.register (method)">register</a></span>, <span class='object_link'><a href="Calculator.html#to_s-instance_method" title="Spree::Calculator#to_s (method)">#to_s</a></span></p>

  
  
  
  
  
  
  
  
  <h3 class="inherited">Methods inherited from <span class='object_link'><a href="Base.html" title="Spree::Base (class)">Base</a></span></h3>
  <p class="inherited"><span class='object_link'><a href="Base.html#page-class_method" title="Spree::Base.page (method)">page</a></span></p>

  
  
  
  
  
  
  
  
  <h3 class="inherited">Methods included from <span class='object_link'><a href="Preferences/Preferable.html" title="Spree::Preferences::Preferable (module)">Preferences::Preferable</a></span></h3>
  <p class="inherited"><span class='object_link'><a href="Preferences/Preferable.html#clear_preferences-instance_method" title="Spree::Preferences::Preferable#clear_preferences (method)">#clear_preferences</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#default_preferences-instance_method" title="Spree::Preferences::Preferable#default_preferences (method)">#default_preferences</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#defined_preferences-instance_method" title="Spree::Preferences::Preferable#defined_preferences (method)">#defined_preferences</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#get_preference-instance_method" title="Spree::Preferences::Preferable#get_preference (method)">#get_preference</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#has_preference%21-instance_method" title="Spree::Preferences::Preferable#has_preference! (method)">#has_preference!</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#has_preference%3F-instance_method" title="Spree::Preferences::Preferable#has_preference? (method)">#has_preference?</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#preference_default-instance_method" title="Spree::Preferences::Preferable#preference_default (method)">#preference_default</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#preference_type-instance_method" title="Spree::Preferences::Preferable#preference_type (method)">#preference_type</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#set_preference-instance_method" title="Spree::Preferences::Preferable#set_preference (method)">#set_preference</a></span></p>

  
  

  <div id="instance_method_details" class="method_details_list">
    <h2>Instance Method Details</h2>

    
      <div class="method_details first">
  <h3 class="signature first" id="available?-instance_method">
  
    - (<tt>Boolean</tt>) <strong>available?</strong>(package) 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    

  </div>
</div>
<div class="tags">
  
<p class="tag_title">Returns:</p>
<ul class="return">
  
    <li>
      
      
        <span class='type'>(<tt>Boolean</tt>)</span>
      
      
      
    </li>
  
</ul>

</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


12
13
14</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'shipping_calculator.rb', line 12</span>

<span class='kw'>def</span> <span class='id identifier rubyid_available?'>available?</span><span class='lparen'>(</span><span class='id identifier rubyid_package'>package</span><span class='rparen'>)</span>
  <span class='kw'>true</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="compute_package-instance_method">
  
    - (<tt>Object</tt>) <strong>compute_package</strong>(package) 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    

  </div>
</div>
<div class="tags">
  
<p class="tag_title">Raises:</p>
<ul class="raise">
  
    <li>
      
      
        <span class='type'>(<tt>NotImplementedError</tt>)</span>
      
      
      
    </li>
  
</ul>

</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


8
9
10</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'shipping_calculator.rb', line 8</span>

<span class='kw'>def</span> <span class='id identifier rubyid_compute_package'>compute_package</span><span class='lparen'>(</span><span class='id identifier rubyid_package'>package</span><span class='rparen'>)</span>
  <span class='id identifier rubyid_raise'>raise</span> <span class='const'>NotImplementedError</span><span class='comma'>,</span> <span class='tstring'><span class='tstring_beg'>&quot;</span><span class='tstring_content'>Please implement &#39;compute_package(package)&#39; in your calculator: </span><span class='embexpr_beg'>#{</span><span class='kw'>self</span><span class='period'>.</span><span class='id identifier rubyid_class'>class</span><span class='period'>.</span><span class='id identifier rubyid_name'>name</span><span class='embexpr_end'>}</span><span class='tstring_end'>&quot;</span></span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="compute_shipment-instance_method">
  
    - (<tt>Object</tt>) <strong>compute_shipment</strong>(shipment) 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    

  </div>
</div>
<div class="tags">
  
<p class="tag_title">Raises:</p>
<ul class="raise">
  
    <li>
      
      
        <span class='type'>(<tt>NotImplementedError</tt>)</span>
      
      
      
    </li>
  
</ul>

</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


4
5
6</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'shipping_calculator.rb', line 4</span>

<span class='kw'>def</span> <span class='id identifier rubyid_compute_shipment'>compute_shipment</span><span class='lparen'>(</span><span class='id identifier rubyid_shipment'>shipment</span><span class='rparen'>)</span>
  <span class='id identifier rubyid_raise'>raise</span> <span class='const'>NotImplementedError</span><span class='comma'>,</span> <span class='tstring'><span class='tstring_beg'>&quot;</span><span class='tstring_content'>Please implement &#39;compute_shipment(shipment)&#39; in your calculator: </span><span class='embexpr_beg'>#{</span><span class='kw'>self</span><span class='period'>.</span><span class='id identifier rubyid_class'>class</span><span class='period'>.</span><span class='id identifier rubyid_name'>name</span><span class='embexpr_end'>}</span><span class='tstring_end'>&quot;</span></span>
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