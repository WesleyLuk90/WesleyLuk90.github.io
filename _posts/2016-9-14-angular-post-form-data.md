---
layout: post
title: Posting FormData with AngularJS
tags:
  angularjs
  webapp
  javascript
  upload
  formdata
---

While it is not very clear from the documentation Angular's $http supports posting FormData. This might just be a quirk of the implementation since its not explicitly stated in the documentation but it works. A quick sample of working code is below.

```
const myFile = getSomeFile();
const myFormData = new FormData();
myFormData.append('image', myFile);
myFormData.append('hello', 'world');
// More info about the config below
$http.post('/my/upload/url', myFormData, { headers: { 'Content-Type': undefined } });
```

One odd issue I ran into was that you must explicitly set 'Content-Type' to undefined. I initially tested using 'multipart/form-data' but my PHP backend was giving me an error.

```
Missing boundary in multipart/form-data POST data in Unknown on line 0
```

I'm unsure why this happens but setting 'Content-Type' to undefined apparently fixes it.