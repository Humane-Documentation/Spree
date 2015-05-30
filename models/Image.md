<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>
  Class: Spree::Image
  
    &mdash; Documentation by YARD 0.8.7.6
  
</title>

  <link rel="stylesheet" href="../css/style.css" type="text/css" charset="utf-8" />

  <link rel="stylesheet" href="../css/common.css" type="text/css" charset="utf-8" />

<script type="text/javascript" charset="utf-8">
  hasFrames = window.top.frames.main ? true : false;
  relpath = '../';
  framesUrl = "../frames.html#!Spree/Image.html";
</script>


  <script type="text/javascript" charset="utf-8" src="../js/jquery.js"></script>

  <script type="text/javascript" charset="utf-8" src="../js/app.js"></script>


  </head>
  <body>
    <div id="header">
      <div id="menu">
  
    <a href="../_index.html">Index (I)</a> &raquo;
    <span class='title'><span class='object_link'><a href="../Spree.html" title="Spree (module)">Spree</a></span></span>
     &raquo; 
    <span class="title">Image</span>
  

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

    <div id="content"><h1>Class: Spree::Image
  
  
  
</h1>

<dl class="box">
  
    <dt class="r1">Inherits:</dt>
    <dd class="r1">
      <span class="inheritName"><span class='object_link'><a href="Asset.html" title="Spree::Asset (class)">Asset</a></span></span>
      
        <ul class="fullTree">
          <li>Object</li>
          
            <li class="next">ActiveRecord::Base</li>
          
            <li class="next"><span class='object_link'><a href="Base.html" title="Spree::Base (class)">Base</a></span></li>
          
            <li class="next"><span class='object_link'><a href="Asset.html" title="Spree::Asset (class)">Asset</a></span></li>
          
            <li class="next">Spree::Image</li>
          
        </ul>
        <a href="#" class="inheritanceTree">show all</a>
      
      </dd>
    
  
  
    
  
    
  
  
  
    <dt class="r2 last">Defined in:</dt>
    <dd class="r2 last">image.rb</dd>
  
</dl>
<div class="clear"></div>








  
    <h2>
      Instance Method Summary
      <small>(<a href="#" class="summary_toggle">collapse</a>)</small>
    </h2>

    <ul class="summary">
      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#find_dimensions-instance_method" title="#find_dimensions (instance method)">- (Object) <strong>find_dimensions</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#mini_url-instance_method" title="#mini_url (instance method)">- (Object) <strong>mini_url</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'>
<p>used by admin products autocomplete.</p>
</div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#no_attachment_errors-instance_method" title="#no_attachment_errors (instance method)">- (Object) <strong>no_attachment_errors</strong> </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'>
<p>if there are errors from the plugin, then add a more meaningful message.</p>
</div></span>
  
</li>

      
    </ul>
  


  
  
  
  
  
  
  
  
  
  
  
  
  
  
  <h3 class="inherited">Methods inherited from <span class='object_link'><a href="Base.html" title="Spree::Base (class)">Base</a></span></h3>
  <p class="inherited"><span class='object_link'><a href="Base.html#page-class_method" title="Spree::Base.page (method)">page</a></span></p>

  
  
  
  
  
  
  
  
  <h3 class="inherited">Methods included from <span class='object_link'><a href="Preferences/Preferable.html" title="Spree::Preferences::Preferable (module)">Preferences::Preferable</a></span></h3>
  <p class="inherited"><span class='object_link'><a href="Preferences/Preferable.html#clear_preferences-instance_method" title="Spree::Preferences::Preferable#clear_preferences (method)">#clear_preferences</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#default_preferences-instance_method" title="Spree::Preferences::Preferable#default_preferences (method)">#default_preferences</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#defined_preferences-instance_method" title="Spree::Preferences::Preferable#defined_preferences (method)">#defined_preferences</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#get_preference-instance_method" title="Spree::Preferences::Preferable#get_preference (method)">#get_preference</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#has_preference%21-instance_method" title="Spree::Preferences::Preferable#has_preference! (method)">#has_preference!</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#has_preference%3F-instance_method" title="Spree::Preferences::Preferable#has_preference? (method)">#has_preference?</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#preference_default-instance_method" title="Spree::Preferences::Preferable#preference_default (method)">#preference_default</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#preference_type-instance_method" title="Spree::Preferences::Preferable#preference_type (method)">#preference_type</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#set_preference-instance_method" title="Spree::Preferences::Preferable#set_preference (method)">#set_preference</a></span></p>

  
  

  <div id="instance_method_details" class="method_details_list">
    <h2>Instance Method Details</h2>

    
      <div class="method_details first">
  <h3 class="signature first" id="find_dimensions-instance_method">
  
    - (<tt>Object</tt>) <strong>find_dimensions</strong> 
  

  

  
</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


29
30
31
32
33
34
35
36</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'image.rb', line 29</span>

<span class='kw'>def</span> <span class='id identifier rubyid_find_dimensions'>find_dimensions</span>
  <span class='id identifier rubyid_temporary'>temporary</span>              <span class='op'>=</span> <span class='id identifier rubyid_attachment'>attachment</span><span class='period'>.</span><span class='id identifier rubyid_queued_for_write'>queued_for_write</span><span class='lbracket'>[</span><span class='symbol'>:original</span><span class='rbracket'>]</span>
  <span class='id identifier rubyid_filename'>filename</span>               <span class='op'>=</span> <span class='id identifier rubyid_temporary'>temporary</span><span class='period'>.</span><span class='id identifier rubyid_path'>path</span> <span class='kw'>unless</span> <span class='id identifier rubyid_temporary'>temporary</span><span class='period'>.</span><span class='id identifier rubyid_nil?'>nil?</span>
  <span class='id identifier rubyid_filename'>filename</span>               <span class='op'>=</span> <span class='id identifier rubyid_attachment'>attachment</span><span class='period'>.</span><span class='id identifier rubyid_path'>path</span> <span class='kw'>if</span> <span class='id identifier rubyid_filename'>filename</span><span class='period'>.</span><span class='id identifier rubyid_blank?'>blank?</span>
  <span class='id identifier rubyid_geometry'>geometry</span>               <span class='op'>=</span> <span class='const'>Paperclip</span><span class='op'>::</span><span class='const'>Geometry</span><span class='period'>.</span><span class='id identifier rubyid_from_file'>from_file</span><span class='lparen'>(</span><span class='id identifier rubyid_filename'>filename</span><span class='rparen'>)</span>
  <span class='kw'>self</span><span class='period'>.</span><span class='id identifier rubyid_attachment_width'>attachment_width</span>  <span class='op'>=</span> <span class='id identifier rubyid_geometry'>geometry</span><span class='period'>.</span><span class='id identifier rubyid_width'>width</span>
  <span class='kw'>self</span><span class='period'>.</span><span class='id identifier rubyid_attachment_height'>attachment_height</span> <span class='op'>=</span> <span class='id identifier rubyid_geometry'>geometry</span><span class='period'>.</span><span class='id identifier rubyid_height'>height</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="mini_url-instance_method">
  
    - (<tt>Object</tt>) <strong>mini_url</strong> 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    
<p>used by admin products autocomplete</p>


  </div>
</div>
<div class="tags">
  

</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


25
26
27</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'image.rb', line 25</span>

<span class='kw'>def</span> <span class='id identifier rubyid_mini_url'>mini_url</span>
  <span class='id identifier rubyid_attachment'>attachment</span><span class='period'>.</span><span class='id identifier rubyid_url'>url</span><span class='lparen'>(</span><span class='symbol'>:mini</span><span class='comma'>,</span> <span class='kw'>false</span><span class='rparen'>)</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="no_attachment_errors-instance_method">
  
    - (<tt>Object</tt>) <strong>no_attachment_errors</strong> 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    
<p>if there are errors from the plugin, then add a more meaningful message</p>


  </div>
</div>
<div class="tags">
  

</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


39
40
41
42
43
44
45
46</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'image.rb', line 39</span>

<span class='kw'>def</span> <span class='id identifier rubyid_no_attachment_errors'>no_attachment_errors</span>
  <span class='kw'>unless</span> <span class='id identifier rubyid_attachment'>attachment</span><span class='period'>.</span><span class='id identifier rubyid_errors'>errors</span><span class='period'>.</span><span class='id identifier rubyid_empty?'>empty?</span>
    <span class='comment'># uncomment this to get rid of the less-than-useful interim messages
</span>    <span class='comment'># errors.clear
</span>    <span class='id identifier rubyid_errors'>errors</span><span class='period'>.</span><span class='id identifier rubyid_add'>add</span> <span class='symbol'>:attachment</span><span class='comma'>,</span> <span class='tstring'><span class='tstring_beg'>&quot;</span><span class='tstring_content'>Paperclip returned errors for file &#39;</span><span class='embexpr_beg'>#{</span><span class='id identifier rubyid_attachment_file_name'>attachment_file_name</span><span class='embexpr_end'>}</span><span class='tstring_content'>&#39; - check ImageMagick installation or image source file.</span><span class='tstring_end'>&quot;</span></span>
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
  Generated on Fri May 15 11:43:00 2015 by
  <a href="http://yardoc.org" title="Yay! A Ruby Documentation Tool" target="_parent">yard</a>
  0.8.7.6 (ruby-2.0.0).
</div>

  </body>
</html>