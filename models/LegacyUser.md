<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>
  Class: Spree::LegacyUser
  
    &mdash; Documentation by YARD 0.8.7.6
  
</title>

  <link rel="stylesheet" href="../css/style.css" type="text/css" charset="utf-8" />

  <link rel="stylesheet" href="../css/common.css" type="text/css" charset="utf-8" />

<script type="text/javascript" charset="utf-8">
  hasFrames = window.top.frames.main ? true : false;
  relpath = '../';
  framesUrl = "../frames.html#!Spree/LegacyUser.html";
</script>


  <script type="text/javascript" charset="utf-8" src="../js/jquery.js"></script>

  <script type="text/javascript" charset="utf-8" src="../js/app.js"></script>


  </head>
  <body>
    <div id="header">
      <div id="menu">
  
    <a href="../_index.html">Index (L)</a> &raquo;
    <span class='title'><span class='object_link'><a href="../Spree.html" title="Spree (module)">Spree</a></span></span>
     &raquo; 
    <span class="title">LegacyUser</span>
  

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

    <div id="content"><h1>Class: Spree::LegacyUser
  
  
  
</h1>

<dl class="box">
  
    <dt class="r1">Inherits:</dt>
    <dd class="r1">
      <span class="inheritName"><span class='object_link'><a href="Base.html" title="Spree::Base (class)">Base</a></span></span>
      
        <ul class="fullTree">
          <li>Object</li>
          
            <li class="next">ActiveRecord::Base</li>
          
            <li class="next"><span class='object_link'><a href="Base.html" title="Spree::Base (class)">Base</a></span></li>
          
            <li class="next">Spree::LegacyUser</li>
          
        </ul>
        <a href="#" class="inheritanceTree">show all</a>
      
      </dd>
    
  
  
    
  
    
      <dt class="r2">Includes:</dt>
      <dd class="r2">UserAddress, UserPaymentSource</dd>
      
    
  
  
  
    <dt class="r1 last">Defined in:</dt>
    <dd class="r1 last">legacy_user.rb</dd>
  
</dl>
<div class="clear"></div>





  <h2>Instance Attribute Summary <small>(<a href="#" class="summary_toggle">collapse</a>)</small></h2>
  <ul class="summary">
    
      <li class="public ">
  <span class="summary_signature">
    
      <a href="#password-instance_method" title="#password (instance method)">- (Object) <strong>password</strong> </a>
    

    
  </span>
  
  
  
    
    
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'>
<p>Returns the value of attribute password.</p>
</div></span>
  
</li>

    
      <li class="public ">
  <span class="summary_signature">
    
      <a href="#password_confirmation-instance_method" title="#password_confirmation (instance method)">- (Object) <strong>password_confirmation</strong> </a>
    

    
  </span>
  
  
  
    
    
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'>
<p>Returns the value of attribute password_confirmation.</p>
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
    
      <a href="#has_spree_role%3F-instance_method" title="#has_spree_role? (instance method)">- (Boolean) <strong>has_spree_role?</strong>(role) </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
    </ul>
  


  
  
  
  
  
  
  
  
  
  
  <h3 class="inherited">Methods inherited from <span class='object_link'><a href="Base.html" title="Spree::Base (class)">Base</a></span></h3>
  <p class="inherited"><span class='object_link'><a href="Base.html#page-class_method" title="Spree::Base.page (method)">page</a></span></p>

  
  
  
  
  
  
  
  
  <h3 class="inherited">Methods included from <span class='object_link'><a href="Preferences/Preferable.html" title="Spree::Preferences::Preferable (module)">Preferences::Preferable</a></span></h3>
  <p class="inherited"><span class='object_link'><a href="Preferences/Preferable.html#clear_preferences-instance_method" title="Spree::Preferences::Preferable#clear_preferences (method)">#clear_preferences</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#default_preferences-instance_method" title="Spree::Preferences::Preferable#default_preferences (method)">#default_preferences</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#defined_preferences-instance_method" title="Spree::Preferences::Preferable#defined_preferences (method)">#defined_preferences</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#get_preference-instance_method" title="Spree::Preferences::Preferable#get_preference (method)">#get_preference</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#has_preference%21-instance_method" title="Spree::Preferences::Preferable#has_preference! (method)">#has_preference!</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#has_preference%3F-instance_method" title="Spree::Preferences::Preferable#has_preference? (method)">#has_preference?</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#preference_default-instance_method" title="Spree::Preferences::Preferable#preference_default (method)">#preference_default</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#preference_type-instance_method" title="Spree::Preferences::Preferable#preference_type (method)">#preference_type</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#set_preference-instance_method" title="Spree::Preferences::Preferable#set_preference (method)">#set_preference</a></span></p>

  
  
  <div id="instance_attr_details" class="attr_details">
    <h2>Instance Attribute Details</h2>
    
      
      <span id="password=-instance_method"></span>
      <div class="method_details first">
  <h3 class="signature first" id="password-instance_method">
  
    - (<tt>Object</tt>) <strong>password</strong> 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    
<p>Returns the value of attribute password</p>


  </div>
</div>
<div class="tags">
  

</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


18
19
20</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'legacy_user.rb', line 18</span>

<span class='kw'>def</span> <span class='id identifier rubyid_password'>password</span>
  <span class='ivar'>@password</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      
      <span id="password_confirmation=-instance_method"></span>
      <div class="method_details ">
  <h3 class="signature " id="password_confirmation-instance_method">
  
    - (<tt>Object</tt>) <strong>password_confirmation</strong> 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    
<p>Returns the value of attribute password_confirmation</p>


  </div>
</div>
<div class="tags">
  

</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


19
20
21</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'legacy_user.rb', line 19</span>

<span class='kw'>def</span> <span class='id identifier rubyid_password_confirmation'>password_confirmation</span>
  <span class='ivar'>@password_confirmation</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
  </div>


  <div id="instance_method_details" class="method_details_list">
    <h2>Instance Method Details</h2>

    
      <div class="method_details first">
  <h3 class="signature first" id="has_spree_role?-instance_method">
  
    - (<tt>Boolean</tt>) <strong>has_spree_role?</strong>(role) 
  

  

  
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


14
15
16</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'legacy_user.rb', line 14</span>

<span class='kw'>def</span> <span class='id identifier rubyid_has_spree_role?'>has_spree_role?</span><span class='lparen'>(</span><span class='id identifier rubyid_role'>role</span><span class='rparen'>)</span>
  <span class='kw'>true</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
  </div>

</div>

    <div id="footer">
  Generated on Fri May 15 11:43:04 2015 by
  <a href="http://yardoc.org" title="Yay! A Ruby Documentation Tool" target="_parent">yard</a>
  0.8.7.6 (ruby-2.0.0).
</div>

  </body>
</html>