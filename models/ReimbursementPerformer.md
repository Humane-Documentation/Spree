<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>
  Class: Spree::ReimbursementPerformer
  
    &mdash; Documentation by YARD 0.8.7.6
  
</title>

  <link rel="stylesheet" href="../css/style.css" type="text/css" charset="utf-8" />

  <link rel="stylesheet" href="../css/common.css" type="text/css" charset="utf-8" />

<script type="text/javascript" charset="utf-8">
  hasFrames = window.top.frames.main ? true : false;
  relpath = '../';
  framesUrl = "../frames.html#!Spree/ReimbursementPerformer.html";
</script>


  <script type="text/javascript" charset="utf-8" src="../js/jquery.js"></script>

  <script type="text/javascript" charset="utf-8" src="../js/app.js"></script>


  </head>
  <body>
    <div id="header">
      <div id="menu">
  
    <a href="../_index.html">Index (R)</a> &raquo;
    <span class='title'><span class='object_link'><a href="../Spree.html" title="Spree (module)">Spree</a></span></span>
     &raquo; 
    <span class="title">ReimbursementPerformer</span>
  

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

    <div id="content"><h1>Class: Spree::ReimbursementPerformer
  
  
  
</h1>

<dl class="box">
  
    <dt class="r1">Inherits:</dt>
    <dd class="r1">
      <span class="inheritName">Object</span>
      
        <ul class="fullTree">
          <li>Object</li>
          
            <li class="next">Spree::ReimbursementPerformer</li>
          
        </ul>
        <a href="#" class="inheritanceTree">show all</a>
      
      </dd>
    
  
  
    
  
    
  
  
  
    <dt class="r2 last">Defined in:</dt>
    <dd class="r2 last">reimbursement_performer.rb</dd>
  
</dl>
<div class="clear"></div>








  
    <h2>
      Class Method Summary
      <small>(<a href="#" class="summary_toggle">collapse</a>)</small>
    </h2>

    <ul class="summary">
      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#perform-class_method" title="perform (class method)">+ (Object) <strong>perform</strong>(reimbursement) </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'>
<p>Actually perform the reimbursement.</p>
</div></span>
  
</li>

      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#simulate-class_method" title="simulate (class method)">+ (Object) <strong>simulate</strong>(reimbursement) </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'>
<p>Simulate performing the reimbursement without actually saving anything or
refunding money, etc.</p>
</div></span>
  
</li>

      
    </ul>
  



  <div id="class_method_details" class="method_details_list">
    <h2>Class Method Details</h2>

    
      <div class="method_details first">
  <h3 class="signature first" id="perform-class_method">
  
    + (<tt>Object</tt>) <strong>perform</strong>(reimbursement) 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    
<p>Actually perform the reimbursement</p>


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
      <pre class="code"><span class="info file"># File 'reimbursement_performer.rb', line 19</span>

<span class='kw'>def</span> <span class='id identifier rubyid_perform'>perform</span><span class='lparen'>(</span><span class='id identifier rubyid_reimbursement'>reimbursement</span><span class='rparen'>)</span>
  <span class='id identifier rubyid_execute'>execute</span><span class='lparen'>(</span><span class='id identifier rubyid_reimbursement'>reimbursement</span><span class='comma'>,</span> <span class='kw'>false</span><span class='rparen'>)</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
      <div class="method_details ">
  <h3 class="signature " id="simulate-class_method">
  
    + (<tt>Object</tt>) <strong>simulate</strong>(reimbursement) 
  

  

  
</h3><div class="docstring">
  <div class="discussion">
    
<p>Simulate performing the reimbursement without actually saving anything or
refunding money, etc. This must return an array of objects that respond to
the following methods:</p>
<ul><li>
<p>#description</p>
</li><li>
<p>#display_amount</p>
</li></ul>

<p>so they can be displayed in the Admin UI appropriately.</p>


  </div>
</div>
<div class="tags">
  

</div><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


14
15
16</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'reimbursement_performer.rb', line 14</span>

<span class='kw'>def</span> <span class='id identifier rubyid_simulate'>simulate</span><span class='lparen'>(</span><span class='id identifier rubyid_reimbursement'>reimbursement</span><span class='rparen'>)</span>
  <span class='id identifier rubyid_execute'>execute</span><span class='lparen'>(</span><span class='id identifier rubyid_reimbursement'>reimbursement</span><span class='comma'>,</span> <span class='kw'>true</span><span class='rparen'>)</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
  </div>

</div>

    <div id="footer">
  Generated on Fri May 15 11:43:08 2015 by
  <a href="http://yardoc.org" title="Yay! A Ruby Documentation Tool" target="_parent">yard</a>
  0.8.7.6 (ruby-2.0.0).
</div>

  </body>
</html>