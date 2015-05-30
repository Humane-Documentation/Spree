<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>
  Class: Spree::Base
  
    &mdash; Documentation by YARD 0.8.7.6
  
</title>

  <link rel="stylesheet" href="../css/style.css" type="text/css" charset="utf-8" />

  <link rel="stylesheet" href="../css/common.css" type="text/css" charset="utf-8" />

<script type="text/javascript" charset="utf-8">
  hasFrames = window.top.frames.main ? true : false;
  relpath = '../';
  framesUrl = "../frames.html#!Spree/Base.html";
</script>


  <script type="text/javascript" charset="utf-8" src="../js/jquery.js"></script>

  <script type="text/javascript" charset="utf-8" src="../js/app.js"></script>


  </head>
  <body>
    <div id="header">
      <div id="menu">
  
    <a href="../_index.html">Index (B)</a> &raquo;
    <span class='title'><span class='object_link'><a href="../Spree.html" title="Spree (module)">Spree</a></span></span>
     &raquo; 
    <span class="title">Base</span>
  

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

    <div id="content"><h1>Class: Spree::Base
  
  
  
</h1>

<dl class="box">
  
    <dt class="r1">Inherits:</dt>
    <dd class="r1">
      <span class="inheritName">ActiveRecord::Base</span>
      
        <ul class="fullTree">
          <li>Object</li>
          
            <li class="next">ActiveRecord::Base</li>
          
            <li class="next">Spree::Base</li>
          
        </ul>
        <a href="#" class="inheritanceTree">show all</a>
      
      </dd>
    
  
  
    
  
    
      <dt class="r2">Includes:</dt>
      <dd class="r2"><span class='object_link'><a href="Preferences/Preferable.html" title="Spree::Preferences::Preferable (module)">Preferences::Preferable</a></span></dd>
      
    
  
  
  
    <dt class="r1 last">Defined in:</dt>
    <dd class="r1 last">base.rb</dd>
  
</dl>
<div class="clear"></div>

<div id="subclasses">
  <h2>Direct Known Subclasses</h2>
  <p class="children"><span class='object_link'><a href="Address.html" title="Spree::Address (class)">Address</a></span>, <span class='object_link'><a href="Adjustment.html" title="Spree::Adjustment (class)">Adjustment</a></span>, <span class='object_link'><a href="Asset.html" title="Spree::Asset (class)">Asset</a></span>, <span class='object_link'><a href="Calculator.html" title="Spree::Calculator (class)">Calculator</a></span>, <span class='object_link'><a href="Classification.html" title="Spree::Classification (class)">Classification</a></span>, <span class='object_link'><a href="Country.html" title="Spree::Country (class)">Country</a></span>, <span class='object_link'><a href="CreditCard.html" title="Spree::CreditCard (class)">CreditCard</a></span>, <span class='object_link'><a href="CustomerReturn.html" title="Spree::CustomerReturn (class)">CustomerReturn</a></span>, <span class='object_link'><a href="InventoryUnit.html" title="Spree::InventoryUnit (class)">InventoryUnit</a></span>, <span class='object_link'><a href="LegacyUser.html" title="Spree::LegacyUser (class)">LegacyUser</a></span>, <span class='object_link'><a href="LineItem.html" title="Spree::LineItem (class)">LineItem</a></span>, <span class='object_link'><a href="LogEntry.html" title="Spree::LogEntry (class)">LogEntry</a></span>, <span class='object_link'><a href="OptionType.html" title="Spree::OptionType (class)">OptionType</a></span>, <span class='object_link'><a href="OptionValue.html" title="Spree::OptionValue (class)">OptionValue</a></span>, <span class='object_link'><a href="Order.html" title="Spree::Order (class)">Order</a></span>, <span class='object_link'><a href="Payment.html" title="Spree::Payment (class)">Payment</a></span>, <span class='object_link'><a href="PaymentCaptureEvent.html" title="Spree::PaymentCaptureEvent (class)">PaymentCaptureEvent</a></span>, <span class='object_link'><a href="PaymentMethod.html" title="Spree::PaymentMethod (class)">PaymentMethod</a></span>, <span class='object_link'><a href="Preference.html" title="Spree::Preference (class)">Preference</a></span>, <span class='object_link'><a href="Price.html" title="Spree::Price (class)">Price</a></span>, <span class='object_link'><a href="Product.html" title="Spree::Product (class)">Product</a></span>, <span class='object_link'><a href="ProductOptionType.html" title="Spree::ProductOptionType (class)">ProductOptionType</a></span>, <span class='object_link'><a href="ProductProperty.html" title="Spree::ProductProperty (class)">ProductProperty</a></span>, <span class='object_link'><a href="Promotion.html" title="Spree::Promotion (class)">Promotion</a></span>, <span class='object_link'><a href="PromotionAction.html" title="Spree::PromotionAction (class)">PromotionAction</a></span>, <span class='object_link'><a href="PromotionActionLineItem.html" title="Spree::PromotionActionLineItem (class)">PromotionActionLineItem</a></span>, <span class='object_link'><a href="PromotionCategory.html" title="Spree::PromotionCategory (class)">PromotionCategory</a></span>, <span class='object_link'><a href="PromotionRule.html" title="Spree::PromotionRule (class)">PromotionRule</a></span>, <span class='object_link'><a href="Property.html" title="Spree::Property (class)">Property</a></span>, <span class='object_link'><a href="Prototype.html" title="Spree::Prototype (class)">Prototype</a></span>, <span class='object_link'><a href="Refund.html" title="Spree::Refund (class)">Refund</a></span>, <span class='object_link'><a href="RefundReason.html" title="Spree::RefundReason (class)">RefundReason</a></span>, <span class='object_link'><a href="Reimbursement.html" title="Spree::Reimbursement (class)">Reimbursement</a></span>, <span class='object_link'><a href="Reimbursement/Credit.html" title="Spree::Reimbursement::Credit (class)">Reimbursement::Credit</a></span>, <span class='object_link'><a href="ReimbursementType.html" title="Spree::ReimbursementType (class)">ReimbursementType</a></span>, <span class='object_link'><a href="ReturnAuthorization.html" title="Spree::ReturnAuthorization (class)">ReturnAuthorization</a></span>, <span class='object_link'><a href="ReturnAuthorizationReason.html" title="Spree::ReturnAuthorizationReason (class)">ReturnAuthorizationReason</a></span>, <span class='object_link'><a href="ReturnItem.html" title="Spree::ReturnItem (class)">ReturnItem</a></span>, <span class='object_link'><a href="Role.html" title="Spree::Role (class)">Role</a></span>, <span class='object_link'><a href="Shipment.html" title="Spree::Shipment (class)">Shipment</a></span>, <span class='object_link'><a href="ShippingCategory.html" title="Spree::ShippingCategory (class)">ShippingCategory</a></span>, <span class='object_link'><a href="ShippingMethod.html" title="Spree::ShippingMethod (class)">ShippingMethod</a></span>, <span class='object_link'><a href="ShippingMethodCategory.html" title="Spree::ShippingMethodCategory (class)">ShippingMethodCategory</a></span>, <span class='object_link'><a href="ShippingRate.html" title="Spree::ShippingRate (class)">ShippingRate</a></span>, <span class='object_link'><a href="State.html" title="Spree::State (class)">State</a></span>, <span class='object_link'><a href="StateChange.html" title="Spree::StateChange (class)">StateChange</a></span>, <span class='object_link'><a href="StockItem.html" title="Spree::StockItem (class)">StockItem</a></span>, <span class='object_link'><a href="StockLocation.html" title="Spree::StockLocation (class)">StockLocation</a></span>, <span class='object_link'><a href="StockMovement.html" title="Spree::StockMovement (class)">StockMovement</a></span>, <span class='object_link'><a href="StockTransfer.html" title="Spree::StockTransfer (class)">StockTransfer</a></span>, <span class='object_link'><a href="Store.html" title="Spree::Store (class)">Store</a></span>, <span class='object_link'><a href="TaxCategory.html" title="Spree::TaxCategory (class)">TaxCategory</a></span>, <span class='object_link'><a href="TaxRate.html" title="Spree::TaxRate (class)">TaxRate</a></span>, <span class='object_link'><a href="Taxon.html" title="Spree::Taxon (class)">Taxon</a></span>, <span class='object_link'><a href="Taxonomy.html" title="Spree::Taxonomy (class)">Taxonomy</a></span>, <span class='object_link'><a href="Tracker.html" title="Spree::Tracker (class)">Tracker</a></span>, <span class='object_link'><a href="Variant.html" title="Spree::Variant (class)">Variant</a></span>, <span class='object_link'><a href="Zone.html" title="Spree::Zone (class)">Zone</a></span>, <span class='object_link'><a href="ZoneMember.html" title="Spree::ZoneMember (class)">ZoneMember</a></span></p>
</div>







  
    <h2>
      Class Method Summary
      <small>(<a href="#" class="summary_toggle">collapse</a>)</small>
    </h2>

    <ul class="summary">
      
        <li class="public ">
  <span class="summary_signature">
    
      <a href="#page-class_method" title="page (class method)">+ (Object) <strong>page</strong>(num) </a>
    

    
  </span>
  
  
  
  
  
  
  

  
    <span class="summary_desc"><div class='inline'></div></span>
  
</li>

      
    </ul>
  


  
  
  
  
  
  
  
  
  <h3 class="inherited">Methods included from <span class='object_link'><a href="Preferences/Preferable.html" title="Spree::Preferences::Preferable (module)">Preferences::Preferable</a></span></h3>
  <p class="inherited"><span class='object_link'><a href="Preferences/Preferable.html#clear_preferences-instance_method" title="Spree::Preferences::Preferable#clear_preferences (method)">#clear_preferences</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#default_preferences-instance_method" title="Spree::Preferences::Preferable#default_preferences (method)">#default_preferences</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#defined_preferences-instance_method" title="Spree::Preferences::Preferable#defined_preferences (method)">#defined_preferences</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#get_preference-instance_method" title="Spree::Preferences::Preferable#get_preference (method)">#get_preference</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#has_preference%21-instance_method" title="Spree::Preferences::Preferable#has_preference! (method)">#has_preference!</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#has_preference%3F-instance_method" title="Spree::Preferences::Preferable#has_preference? (method)">#has_preference?</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#preference_default-instance_method" title="Spree::Preferences::Preferable#preference_default (method)">#preference_default</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#preference_type-instance_method" title="Spree::Preferences::Preferable#preference_type (method)">#preference_type</a></span>, <span class='object_link'><a href="Preferences/Preferable.html#set_preference-instance_method" title="Spree::Preferences::Preferable#set_preference (method)">#set_preference</a></span></p>

  
  

  <div id="class_method_details" class="method_details_list">
    <h2>Class Method Details</h2>

    
      <div class="method_details first">
  <h3 class="signature first" id="page-class_method">
  
    + (<tt>Object</tt>) <strong>page</strong>(num) 
  

  

  
</h3><table class="source_code">
  <tr>
    <td>
      <pre class="lines">


9
10
11</pre>
    </td>
    <td>
      <pre class="code"><span class="info file"># File 'base.rb', line 9</span>

<span class='kw'>def</span> <span class='kw'>self</span><span class='period'>.</span><span class='id identifier rubyid_page'>page</span> <span class='id identifier rubyid_num'>num</span>
  <span class='id identifier rubyid_send'>send</span> <span class='const'>Kaminari</span><span class='period'>.</span><span class='id identifier rubyid_config'>config</span><span class='period'>.</span><span class='id identifier rubyid_page_method_name'>page_method_name</span><span class='comma'>,</span> <span class='id identifier rubyid_num'>num</span>
<span class='kw'>end</span></pre>
    </td>
  </tr>
</table>
</div>
    
  </div>

</div>

    <div id="footer">
  Generated on Fri May 15 11:42:58 2015 by
  <a href="http://yardoc.org" title="Yay! A Ruby Documentation Tool" target="_parent">yard</a>
  0.8.7.6 (ruby-2.0.0).
</div>

  </body>
</html>