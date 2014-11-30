---
layout: post
title:  "Reinitializing jquery event on ajax response"
date:   2012-01-31 13:20:00
categories: JavaScript
---

I had a jquery change event attached to a checkbox which was part of a div.
<pre lang="html4strict" escaped="true">&lt;div id="test-div"&gt;
&lt;input type="checkbox" checked="checked" value="1" class="test-chkbox" /&gt;
&lt;/div&gt;</pre>
Using the following jquery code a change event was attached to the above checkbox
<pre lang="javascript">$(".test-chkbox").change(function () {
$.ajax({
type: "GET",
url: "some-action",
data: this.value,
cache: false,
success: function(response){
$("#test-div").replaceWith(response);
}
});
});</pre>
Response of ajax contained the same checkbox but the change event was no more attached to it, so to solve the  issue I changed jQuery code as specified below.
<pre lang="javascript">$(document).on("change", ".test-chkbox", function () {
$.ajax({
type: "GET",
url: "some-action",
data: this.value,
cache: false,
success: function(response){
$("#test-div").replaceWith(response);
}
});
});</pre>
The above change made sure that the change event is always attached to checkbox even after the ajax response.

Note: Older versions of jQuery use **.delegate** and **.live** instead of .**on**