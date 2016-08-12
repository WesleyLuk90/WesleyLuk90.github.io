---
layout: post
title: Sending Data to the Frontend
tags:
  javascript
  webapp
---

Heres the setup, you're building your web application and you have complex data in the backend you need to get to the front end. You want that data as a javascript object (i.e. you'll probably use JSON). What are your options?

1. Dump JSON strings into a global variable in a &lt;script> tag
2. Dump JSON strings as html data attributes
3. Separate AJAX call to fetch data

## Dump JSON strings into a global variable in a &lt;script> tag

Embed a script tag onto your page and output the data as JSON. Since JSON is valid JavaScript it will be parsed as an object automatically.

```
<script>
	var myData = <?php echo json_encode($some_object_here) ?>;
</script>
```

### Pros
* Simple to do and easy to understand
* Faster than making a separate AJAX call
* No manual JSON parsing needed

### Cons
* Your data is stored as a global variable, data is just floating around on the page
* You must be sure that you don't access your data before the browser parses it (i.e. wait for DOMContentLoaded or insert your JavaScript after that tag)
* Might be impossible to escape properly? How do you escape a string containing &lt;/script>?
* Page loading will appear blocked if there is a large amount of data
* If data is dynamic it can not be cached

## Dump JSON strings as html data attributes
When you render your html, set the data attribute as

```
<?php
	$escaped_data = htmlspecialchars(json_encode($some_object_here));
?>
<div data-some-info="<?php echo $escaped_data ?>">
</div>
```

### Pros
* Simple to do and easy to understand
* Faster than making a separate AJAX call
* Built in parsing from jQuery with $.data('some-info')

### Cons
* Extra escaping needed
* Page loading will appear blocked if there is a large amount of data
* If data is dynamic it can not be cached

### Other notes
* Data is tied to an element which can be more helpful contextually (e.g. Putting the data for a table on the table element)

## Separate AJAX call to fetch data
Once your javascript is loaded, send an AJAX call to a separate endpoint on your backend and fetch the data

### Pros
* Cleanest option, you have a specific endpoint to get data
* More reusable
* Can display progress/loading while loading data
* Initial page load isn't delayed

### Cons
* Overhead of an extra http requests
* Need to be more careful about when you use the data, have to wait for AJAX call to come back

## Conclusion
In most of my applications I usually decide between _Dump JSON strings as html data attributes_ and _Separate AJAX call to fetch data_. Which one I pick depends on the application requirements, if theres lots of data usually an AJAX call is better but if the data is small I will just embed it into the page.