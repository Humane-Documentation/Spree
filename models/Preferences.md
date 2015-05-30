<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>
  Module: Spree::Preferences
  
    &mdash; Documentation by YARD 0.8.7.6
  
</title>

  <link rel="stylesheet" href="../css/style.css" type="text/css" charset="utf-8" />

  <link rel="stylesheet" href="../css/common.css" type="text/css" charset="utf-8" />

<script type="text/javascript" charset="utf-8">
  hasFrames = window.top.frames.main ? true : false;
  relpath = '../';
  framesUrl = "../frames.html#!Spree/Preferences.html";
</script>


  <script type="text/javascript" charset="utf-8" src="../js/jquery.js"></script>

  <script type="text/javascript" charset="utf-8" src="../js/app.js"></script>


  </head>
  <body>
    <div id="header">
      <div id="menu">
  
    <a href="../_index.html">Index (P)</a> &raquo;
    <span class='title'><span class='object_link'><a href="../Spree.html" title="Spree (module)">Spree</a></span></span>
     &raquo; 
    <span class="title">Preferences</span>
  

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

    <div id="content"><h1>Module: Spree::Preferences
  
  
  
</h1>

<dl class="box">
  
  
    
  
    
  
  
  
    <dt class="r1 last">Defined in:</dt>
    <dd class="r1 last">preferences/configuration.rb<span class="defines">,<br />
  preferences/store.rb,<br /> preferences/scoped_store.rb,<br /> preferences/preferable_class_methods.rb</span>
</dd>
  
</dl>
<div class="clear"></div>

<h2>Overview</h2><div class="docstring">
  <div class="discussion">
    
<p>This takes the preferrable methods and adds some syntatic sugar to access
the preferences</p>

<p>class App &lt; Configuration</p>

<pre class="code ruby"><code class="ruby"><span class='id identifier rubyid_preference'>preference</span> <span class='symbol'>:color</span><span class='comma'>,</span> <span class='symbol'>:string</span>
</code></pre>

<p>end</p>

<p>a = App.new</p>

<p>setters: a.color = :blue <a href=":color">a</a> = :blue a.set :color =
:blue a.preferred_color = :blue</p>

<p>getters: a.color <a href=":color">a</a> a.get :color a.preferred_color</p>


  </div>
</div>
<div class="tags">
  

</div><h2>Defined Under Namespace</h2>
<p class="children">
  
    
      <strong class="modules">Modules:</strong> <span class='object_link'><a href="Preferences/Preferable.html" title="Spree::Preferences::Preferable (module)">Preferable</a></span>, <span class='object_link'><a href="Preferences/PreferableClassMethods.html" title="Spree::Preferences::PreferableClassMethods (module)">PreferableClassMethods</a></span>
    
  
    
      <strong class="classes">Classes:</strong> <span class='object_link'><a href="Preferences/Configuration.html" title="Spree::Preferences::Configuration (class)">Configuration</a></span>, <span class='object_link'><a href="Preferences/ScopedStore.html" title="Spree::Preferences::ScopedStore (class)">ScopedStore</a></span>, <span class='object_link'><a href="Preferences/Store.html" title="Spree::Preferences::Store (class)">Store</a></span>, <span class='object_link'><a href="Preferences/StoreInstance.html" title="Spree::Preferences::StoreInstance (class)">StoreInstance</a></span>
    
  
</p>









</div>

    <div id="footer">
  Generated on Fri May 15 11:42:58 2015 by
  <a href="http://yardoc.org" title="Yay! A Ruby Documentation Tool" target="_parent">yard</a>
  0.8.7.6 (ruby-2.0.0).
</div>

  </body>
</html>