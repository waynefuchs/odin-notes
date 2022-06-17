# Forms

## Links

[UX Form Design for Mobile](https://www.smashingmagazine.com/2018/08/ux-html5-mobile-form-part-1/)

[Web Form Usability](https://www.smashingmagazine.com/2011/11/extensive-guide-web-form-usability/)

[Styling Checkbox](https://moderncss.dev/pure-css-custom-checkbox-style/)


## Recommended CSS

``` css
/* this ensures that font features are inherited, which is not a given on all browsers */
button, input, select, textarea {
  font-family: inherit;
  font-size: 100%;
}
```

## Example of most form elements

``` html
<form action="myscript.cgi" method="post">

    <!-- input options -->
    <!-- readonly: cannot be modified, data is sent onSubmit() -->
    <!-- disabled: cannot be modified, data is not sent onSubmit() -->
    <!-- size="box size" -->
    <!-- maxlength="number of characters you can enter into the box" -->
    <!-- spellcheck="true/false" to turn spell check for the box on / off -->
    <fieldset class="formgroup">
        <legend>Input Types</legend>
        <div>
            <p><label for="someField">What The Label Says Here</label></p>
            <input
                type="text"
                id="someField"
                name="someFieldBackendVariableName"
                placeholder="text">
            <!-- the `multiple` keyword can be used to allow multiple addresses, separated by commas -->
            <input type="email" placeholder="email">        <!-- changes mobile keyboard to make it easier, does simple email validation -->
            <input type="password" placeholder="password">  <!-- hide the input as the user types it -->
            <input type="number" placeholder="number">      <!-- [min, max, step] ignores any values except number characters -->
            <input type="search" placeholder="search">      <!-- rounded corners + an 'x' to clear results -->
        </div>

        <div>
            <input type="tel" placeholder="telephone">      <!-- on mobile keyboard is displayed as phone pad -->
            <input type="url" placeholder="url">            <!-- browser ensures valid url (NOT that it exists) and mobile keyboard changes -->                
            <input type="text" list="suggestions" 
                placeholder="autocomplete box">             <!-- kind of like a drop down -->
            <datalist id="suggestions">
                <option>Apple</option>
                <option>Banana</option>
                <option>Cherry</option>
                <option>Watermelon</option>
            </datalist>
            <input type="color" name="color" id="color">    <!-- color picker -->
        </div>

        <div>
            <input type="date">                             <!-- gives the user a date input -->
            <input type="hidden">                           <!-- place to put variables you don't want the user to see -->
            <input type="image" src="" alt="image button">  <!-- looks like an <img> but behaves like a <button> -->
        </div>


        <div><input type="file">                             <!-- allow a user to select a local file --></div>

        <!-- on mobile the "file" type can allow the user to upload an image/video/audio clip -->
        <div><input type="file" accept="image/*;capture=camera"></div>
        <div><input type="file" accept="video/*;capture=camcorder"></div>
        <div><input type="file" accept="audio/*;capture=microphone"></div>
    </fieldset>

    <!-- textarea (text box) -->
    <fieldset class="formgroup">
        <legend>Text Area</legend>
        <textarea rows="20" cols="80">Initial Content</textarea>
    </fieldset>

    <!-- select (drop down menu) -->
    <!-- can add `multiple` property to turn it into a list -->
    <fieldset class="formgroup">
        <legend>Drop Down Menu</legend>
        <select name="backendVariableNameForDropdown">
            <optgroup label="First Two">
                <option value="aValueForBackend">What shows in dropdown</option>
                <option value="bValueForBackend" selected>This is the default option</option>
            </optgroup>
            <option value="cValueForBackend">And this is also an option</option>
        </select>
    </fieldset>

    <!-- radio group -->
    <fieldset class="formgroup">
        <legend>Radio Group</legend>
        <h2>Pick One From the Radio Group</h2>
        <div>
            <input type="radio" name="groupName" id="aBackendVariableName" value="aBackendVariableValue">
            <label for="aBackendVariableName">This is Variable and Value A</label>
        </div>
        <div>
            <input type="radio" name="groupName" id="bBackendVariableName" value="cBackendVariableValue" checked>
            <label for="aBackendVariableName">I want you to pick Option B!</label>
        </div>
        <div>
            <input type="radio" name="groupName" id="cBackendVariableName" value="cBackendVariableValue">
            <label for="aBackendVariableName">C if you really have to</label>
        </div>
    </fieldset>

    <!-- checkbox group -->
    <fieldset class="formgroup">
        <legend>Checkboxes</legend>
        <div>
            <input type="checkbox" name="checkboxGroup" id="aCheckName" value="aCheckValue">
            <label for="aCheckName">It a Checkbox! (a)</label>
        </div>
        <div>
            <input type="checkbox" name="checkboxGroup" id="bCheckName" value="bCheckValue">
            <label for="bCheckName">Use a single checkbox if you want a true/false bool</label>
        </div>
        <div>
            <input type="checkbox" name="checkboxGroup" id="cCheckName" value="cCheckValue" checked>
            <label for="cCheckName">The last checkbox... (c)</label>
        </div>
    </fieldset>

    <!-- Buttons -->
    <fieldset class="formgroup">
        <legend>Button Demo</legend>
        <button>Button Text</button><!-- type="button" is implied -->
        <button type="submit">Submit Text</button>
        <button type="reset">Reset Text</button>
    </fieldset>

    <!-- Progress Bar --> 
    <fieldset class="formgroup">
        <legend>Meters and Progress Bar</legend>
        <p>
            <progress id="progress" max="100" value="75">75/100</progress>
        </p>
        <p>
            <meter min="0" max="100" value="75" low="33" high="66" optimum="50">75</meter>
        </p>

        <p>
            <input type="range" name="price" id="price" min="50000" max="500000" step="100" value="250000">
            <output class="price-output" for="price"></output>
        </p>
    </fieldset>

</form>


<script>
    const price = document.querySelector('#price');
    const output = document.querySelector('.price-output');
    
    console.log(price);
    console.log(output);
    output.textContent = price.value;
    
    price.addEventListener('input', function() {
        output.textContent = price.value;
    });
</script>
```

## Action

The url to send the form to.

## Method

GET: Get something from the server; as in "GET the results from the server for this search query"
POST: Send data to the server; as in "POST this comment to this social media site."

Select which HTTP request method to use.
[HTTP Methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)