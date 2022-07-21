- [Forms](#forms)
  - [Links](#links)
  - [Properties](#properties)
    - [Action](#action)
    - [Method](#method)
  - [Recommended CSS](#recommended-css)
  - [Input](#input)
    - [`type`](#type)
    - [Other Input Attributes](#other-input-attributes)
  - [Example of most form elements](#example-of-most-form-elements)
  - [Form Validation](#form-validation)
    - [Adherence to Input Type](#adherence-to-input-type)
    - [`required`](#required)
    - [`minlength` and `maxlength`](#minlength-and-maxlength)
    - [`min` and `max`](#min-and-max)
    - [`pattern`](#pattern)
    - [`title`](#title)
    - [`placeholder`](#placeholder)
  - [Pseudo-Classes](#pseudo-classes)

# Forms

## Links

[UX Form Design for Mobile](https://www.smashingmagazine.com/2018/08/ux-html5-mobile-form-part-1/)

[Web Form Usability](https://www.smashingmagazine.com/2011/11/extensive-guide-web-form-usability/)

[Styling Checkbox](https://moderncss.dev/pure-css-custom-checkbox-style/)

[ClientSide: Validating Forms Using Javascript](https://developer.mozilla.org/en-US/docs/Learn/Forms/Form_validation#validating_forms_using_javascript)

[Form Validation UX](https://css-tricks.com/form-validation-ux-html-css/)

## Properties

### Action

The url to send the form to.

### Method

GET: Get something from the server; as in "GET the results from the server for this search query"
POST: Send data to the server; as in "POST this comment to this social media site."

Select which HTTP request method to use.
[HTTP Methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)

## Recommended CSS

``` css
/* this ensures that font features are inherited, which is not a given on all browsers */
button, input, select, textarea {
  font-family: inherit;
  font-size: 100%;
}
```

## Input

### `type`

| type | description |
| ---- | ----------- |
| `button` | a button with no default behavior |
| `checkbox` | a check/tick box |
| `color` | a color picker |
| `date` | a date picker for the year, month, and day |
| `datetime-local` | a date and time picker |
| `email` | an email entry field |
| `file` | a file picker |
| `hidden` | a hidden field |
| `image` | a button which displays the image defined by the src attribute |
| `month` | a month and year picker |
| `number` | a number entry field |
| `password` | a password entry field with obscured text |
| `radio` | a radio button |
| `range` | a slider control |
| `reset` | a button that resets all form inputs to their default values (but avoid using this, as it’s rarely useful) |
| `search` | a search entry field |
| `submit` | a form submission button |
| `tel` | a telephone number entry field |
| `text` | a text entry field |
| `time` | a time picker with no time zone |
| `url` | a URL entry field |
| `week` | a week number and year picker |

### Other Input Attributes

| attribute | description |
| --------- | ----------- |
| `accept` | file upload type |
| `alt` | alternative text for the image types |
| `autocomplete` | hint for field auto-completion |
| `autofocus` | focus field on page load |
| `capture` | media capture input method |
| `checked` | checkbox/radio is checked |
| `disabled` | disable the control (it won’t be validated or have its value submitted) |
| `form` | associate with a form using this ID |
| `formaction` | URL for submission on submit and image buttons |
| `inputmode` | data type hint |
| `list` | ID of <datalist> autocomplete options |
| `max` | maximum value |
| `maxlength` | maximum string length |
| `min` | minimum value |
| `minlength` | minimum string length |
| `name` | name of control, as submitted to server |
| `pattern` | a regular expression pattern, such as [A-Z]+ for one or more uppercase characters |
| `placeholder` | placeholder text when the field value is empty |
| `readonly` | the field is not editable, but it will still be validated and submitted |
| `required` | the field is required |
| `size` | the size of the control (often overridden in CSS) |
| `spellcheck` | set true or false spell-checking |
| `src` | image URL |
| `step` | incremental values in numbers and ranges |
| `type` | field type (see above) |
| `value` | the initial value |

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


## Form Validation

Keep in mind that the HTML can be edited by the user, so back-end validation **must** be performed.


### Adherence to Input Type

> "Please enter a valid email address" (the data you entered is not in the right format).

### `required`

Attribute to make a field required before the form is submitted.

> "This field is required" (You can't leave this field blank).

``` html
<input type="email" id="user_email" name="user_email" required>
```

### `minlength` and `maxlength`

Attributes to require length requirements.

``` html
<input type="email" id="user_email" name="user_email" minlength="7" maxlength="120">
```

### `min` and `max`

Attributes to require a number in a range

``` html
<input type="number" id="numx" name="numx" min="100" max="200">
```

### `pattern`

Attribute to force a match to a regular expression.

Can only be used on `<input>` elements.

> "Please enter your zip code in the format xxxxx-xxxx" (A specific data format is required for it to be considered valid).
> 
> "Your password needs to be between 8 and 30 characters long and contain one uppercase letter, one symbol, and a number." (A very specific data format is required for your data).

``` html
<input type="text" id="zip_code" name="zip_code" pattern="(\d{5}([\-]\d{4})?)" required>
```

### `title`

Attribute to provide a helpful message when validation is incorrect. Prior to submission, this is a mouse-over effect. When submit is pressed, a message connected to the text box pops up to provide assistance.

``` html
<input type="text" id="zip_code" name="zip_code" pattern="(\d{5}([\-]\d{4})?)" title="Please enter a valid zip code, example: 65251" required>
```

### `placeholder`

An attribute to provide example text. This should be used only when formatting assistance is absolutely necessary.


## Pseudo-Classes

See: css/Pseudo-Classes.md