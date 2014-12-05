---
layout: post
title:  "Reinitializing jquery event on ajax response"
date:   2012-01-31 13:20:00
categories: JavaScript
---

I had a jquery change event attached to a checkbox which was part of a div.

``` html
<div id="test-div">
<input type="checkbox" checked="checked" value="1" class="test-chkbox" />
</div>
```

Using the following JQuery code a change event was attached to the above check-box

``` javascript
$(".test-chkbox").change(function () {
	$.ajax({
		type: "GET",
		url: "some-action",
		data: this.value,
		cache: false,
		success: function(response) {
			$("#test-div").replaceWith(response);
		}
	});
});
```
Response of ajax contained the same check-box but the change event was no more attached to it, so to solve the issue I changed jQuery code as specified below.

``` javascript
$(document).on("change", ".test-chkbox", function () {
	$.ajax({
		type: "GET",
		url: "some-action",
		data: this.value,
		cache: false,
		success: function(response) {
			$("#test-div").replaceWith(response);
		}
	});
});
```

The above change made sure that the change event is always attached to check-box even after the ajax response.

Note: Older versions of jQuery use **.delegate** and **.live** instead of .**on**