---
layout: default
group: fedg
subgroup: Javascript
title: jQuery loader widget
menu_title: jQuery loader widget
menu_order: 4
github_link: frontend-dev-guide/javascript/jquery-widget-loader.md
---

<h2 id="fedg_loader_widget_overview">Overview</h2>

The loader widget blocks some or all page content when an Ajax request is being sent; however, you can also use it for non-Ajax tasks.

The loader source is `<your Magento install dir>/pub/lib/mage/loader.js`.

<h2 id="fedg_loader_init">Initialize the loader widget</h2>

Example:

<pre>$('[data-container="some-location"]').loader({
    icon: 'icon.gif',
    texts: {
        loaderText: 'Please wait...',
        imgAlt: 'Loading...'
    }
});</pre>

<h2 id="fedg_loader_options">Options for the loader widget</h2>

The loader widget has the following options:

*	<a href="#fedg_loader_options-icon">icon</a>
*	<a href="#fedg_loader_options-text">texts</a>
*	<a href="#fedg_loader_options-template">template</a>

<h4 id="fedg_loader_options-icon">icon</h4>

The URL to the loader image. This image is displayed when the widget is active; that is, between the `ajaxSend` and `ajaxComplete` events.

**Type**: String
**Default value**: No image by default.

<h4 id="fedg_loader_options-text">texts</h4>

An object that contains translations for loader text:

*	`texts.loaderText`

	The text that is displayed under the loader image.

	Default value: `Please wait...`

*	`texts.imgAlt`

	The text that is set as the `alt` attribute value of the loader image.
	Default value: Loading...

<h4 id="fedg_loader_options-template">template</h4>

HTML wrapper for output, or a DOM element selector.

Default value:

<script src="https://gist.github.com/xcomSteveJohnson/0cfe5b6cc79bd36cea5b.js"></script>

<h2 id="fedg_loader_details">Implement the loader widget</h2>

The loader widget is automatically subscribed to the `ajaxSend` and `ajaxComplete` events, although it can also be triggered manually using the `processStart` and `processStop` events.

To enable the loader for an Ajax request, set the `showLoader` Ajax call option to `true`.

See the following sections for more information:

*	<a href="#fedg_loader_details_block-part">Use the loader to block page content</a>
*	<a href="#fedg_loader_details_non-ajax">Use the loader for Ajax and non-Ajax calls</a>

<h3 id="fedg_loader_details_block-part">Use the loader to block page content</h3>

The loader can be used to lock all page content, or only lock certain forms or certain blocks. Specify the elements to be blocked using the `loaderContext` Ajax call option.

In the following example, an Ajax request loader is triggered and set to block only the element for which the `date-role` attribute value is `translation-form`:

<pre>jQuery.ajax({
    url: url,
    type: 'POST',
    data: parameters,
    showLoader: true,
    loaderContext: '[data-role="translation-form"]'
})</pre>

<h3 id="fedg_loader_details_non-ajax">Use the loader for Ajax and non-Ajax calls</h3>

To have the loader to span multiple Ajax calls or to show it when non-Ajax tasks are underway, trigger it manually:

<pre>...
$(this.element).trigger("processStart");
// do multiple ajax calls
// or other work
$(this.element).trigger("processStop");</pre>

Where `this.element` is the element on which the loader is dependent.

#### Related topics

*	<a href="{{ site.gdeurl }}frontend-dev-guide/javascript/jquery-widgets-about.html">Magento jQuery widgets</a>
*	<a href="{{ site.gdeurl }}frontend-dev-guide/javascript/jquery-widget-calendar.html">jQuery calendar widget</a>
*	<a href="{{ site.gdeurl }}frontend-dev-guide/javascript/jquery-widget-tabs.html">jQuery tabs widget</a>
*	<a href="{{ site.gdeurl }}frontend-dev-guide/javascript/jquery-widget-translate-inline.html">jQuery translateInline widget</a>
*	<a href="{{ site.gdeurl }}coding-standards/code-standard-jquery-widgets.html">jQuery widget coding standard</a>