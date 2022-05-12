# MultiForm Svelte Component

## How to use:
 - Drag and drop the `MultiForm.svelte` into your project where you store your components.
 - Import into the page you want it to appear on (`import MultiForm from '../path/to/component'`) and include it in your markup using the following syntax `<MultiForm />`

-----

## Configuration
 - To edit the core properties of the form you do so by providing a `formOptions` object to the Modular Form. `<MultiFormMultiForm bind:formOptions={formOptions} />`

 - To apply custom styles a `formStyles` object must be provided to the Modular Form. `<MultiForm bind:formStyles={formStyles} />`

 - When the form is submitted a custom `formSubmitted` event is dispatched from the Modular Form. This event passes through an array of the names and values of each of the inputs inside the form.`<MultiForm on:formSubmitted={formSubmitted} />`

-----

## FormOptions Object Structure
```javascript
{
    formTitle: "",
    formItems: [], 
    submitButtonText: ""
} 
```

Form Items are specified in the following format
```javascript
{
    type: 'type of input',
    name: 'name of input (optional but recommended)'
    label: 'label for input (optional)',
    placeholder: 'placeholder for input (optional)',
    isRequired: true/false '(optional)'
}
```
**NOTE: If no name is specified the input will be given a name that follows the following convention. 'form-item-(input-type or text)-(index of the input in the formItems array inside formOptions)'**

-----

## Customization
There are 4 different sections of the form you can style, these include the form container, form title, form inputs, and the form submit button. The following is the structure of the `formStyles` object. 

**NOTE: All values must be strings! Also any property that isn't provided will fallback to default styling**
```javascript
{
    container: {
        width: "22rem",
        padding: "1em 2em",
        margin: "1rem 0",
        gap: "1rem",
        borderColor: "grey",
        borderWidth: "1px",
        borderStyle: "solid",
        borderRadius: "10px",
        backgroundColor: "#f5f5f5",
        fontFamily: "'Trebuchet MS', sans-serif"
    },
    title:{
        fontSize: "32pt",
        margin: "0.4rem auto",
        padding: "0",
        fontWeight: "bold",
	fontColor: "black",
        textDecoration: "none",
    },
    inputs:{
        width: "22rem",
        height: "3rem",
        padding: "0.4em 0 0.4 1.4em",
        margin: "0rem",
        gap: "0.6rem",
        fontSize: '14pt',
	fontColor: "black",
        borderColor: "grey",
        borderWidth: "1px",
        borderStyle: "solid",
        borderRadius: "10px",
        backgroundColor: "#f5f5f5",
        hoverBackgroundColor: "#dbdbdb",
        focusBorderColor: '#0022c9',
        transition: 'border-color ease-in-out 200ms, background-color ease-in-out 200ms, outline ease-in-out 200ms',
        label:{
            fontSize: '14pt',
            fontWeight: 'normal',
            textDecoration: 'none',
			fontColor: "black",
        }
    },
    button:{
        width: "10rem",
        height: "3rem",
        padding: "0",
        margin: "0 auto",
        fontSize: "16pt",
	fontColor: "black",
        textAlign: "center",
        borderColor: "grey",
        borderWidth: "1px",
        borderStyle: "solid",
        borderRadius: "10px",
        backgroundColor: "#ffffff",
        hoverBackgroundColor: "#dbdbdb",
        transition: 'border-color ease-in-out 200ms, background-color ease-in-out 200ms, outline ease-in-out 200ms'
    }
}
```

-----

## Handling Form Submission
When the form is submitted a `formSubmitted` event is called, passed with this event are the values of the form in the format of an array of object. Each input value object is setup as follow, `[{name: 'input-name', value: 'input-value'}, ...]`

To access these values you need to access the `detail` property on the event object.

Example:
```javascript
const formSubmitted = (event)=>{
    const formData = event.detail;
}
```

-----

## Form Slots
You are able to further customize the form by taking advantage of the slots provided. There are 4 slots included inside the form, 2 on the outside of the form container on the top and bottom, and 3 inside the form container, 1 between the title and first input, 1 between the last input and submit button and 1 between the submit button and the bottom of the form. The naming of theses slots are as follows, `form-outter-(top/bottom)-slot`, and `form-inner-(top)-slot`, `form-inner-bottom-slot`, and `form-inner-bottom-slot-two`. The structure of the element inside your markup would look like the following with all slots included.

```html
<MultiForm>
    <div slot="form-outter-top-slot">
    </div>

    <div slot="form-inner-top-slot">
    </div>

    <div slot="form-inner-bottom-slot">
    </div>

    <div slot="form-inner-bottom-slot-two">
    </div>

    <div slot="form-outter-bottom-slot">
    </div>
</MultiForm>
```
