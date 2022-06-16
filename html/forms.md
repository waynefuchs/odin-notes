# Forms

``` html
<form action="myscript.cgi" method="post">
    ...form control elements...
    <label for="someField">What The Label Says Here</label>
    <input type="text" id="someField">
</form>
```

## Action

The url to send the form to.

## Method

GET: Get something from the server; as in "GET the results from the server for this search query"
POST: Send data to the server; as in "POST this comment to this social media site."

Select which HTTP request method to use.
[HTTP Methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)