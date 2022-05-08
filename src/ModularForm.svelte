<script>
    import { onMount, createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

    //Default fallback options for the form
    const defaultOptions = {
        title: "Example",
        items: [
            {type: "text", label: "Name", isRequired: true},
            {type: "email", label: "Email", isRequired: true},
            {type: "date", label: "Date of Birth", isRequired: true},
        ],
        submitText: "Submit"
    }

    //Default fallback styling for the form
    const defaultStyling = {
        container: {
            width: "22rem",
            padding: "1em 2em",
            margin: "1rem 0",
            gap: "1rem",
            borderColor: "grey",
            borderWidth: "1px",
            borderStyle: "solid",
            borderRadius: "10px",
            backgroundColor: "#f5f5f5"
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

    //Exported formOptions used to assign custom core info to the form
    export let formOptions = {
        formTitle: defaultOptions.title,
        formItems: defaultOptions.items,
        submitButtonText: defaultOptions.submitText,
    }

    //Exported formStyles used to assign custom styling to the form
    export let formStyles = defaultStyling;

    //Mount function that calls the applyStyles function once the component is mounted to the page 
    onMount(()=>{
        applyStyles();
    });

    //Function to apply the specified styling to the form
    const applyStyles = ()=>{
        //Main Form Styling
        const modularForms = document.querySelectorAll('.modular-form');
            
        if(modularForms){
            for (let i = 0; i < modularForms.length; i++) {
                const form = modularForms[i];
                form.style.width = formStyles.container.width || defaultStyling.container.width;
                form.style.padding = formStyles.container.padding || defaultStyling.container.padding;
                form.style.margin = formStyles.container.margin || defaultStyling.container.margin;
                form.style.gap = formStyles.container.gap || defaultStyling.container.gap;
                form.style.border = `${formStyles.container.borderWidth} ${formStyles.container.borderStyle} ${formStyles.container.borderColor}` || `${defaultStyling.container.borderWidth} ${defaultStyling.container.borderStyle} ${defaultStyling.container.borderColor}`;
                form.style.borderRadius = formStyles.container.borderRadius || defaultStyling.container.borderRadius;
                form.style.backgroundColor = formStyles.container.backgroundColor || defaultStyling.container.backgroundColor;
            }
        }

        //Form Title Styling
        const formTitles = document.querySelectorAll('.form-title');

        if(formTitles){
            for (let i = 0; i < formTitles.length; i++) {
                const titles = formTitles[i];
            
                titles.style.fontSize = formStyles.title.fontSize || defaultStyling.title.fontSize;
                titles.style.textDecoration = formStyles.title.textDecoration || defaultStyling.title.textDecoration;
                titles.style.textAlign = formStyles.title.textDecoration || defaultStyling.title.textDecoration;
                titles.style.margin = formStyles.title.margin || defaultStyling.title.margin;
                titles.style.padding = formStyles.title.padding || defaultStyling.title.padding;
                titles.style.fontWeight = formStyles.title.fontWeight || defaultStyling.title.fontWeight;
                titles.style.color = formStyles.title.fontColor || defaultStyling.title.fontColor;
            }
        }

        //Input Containers Styling
        const formContainers = document.getElementsByClassName('input-container');

        if(formContainers){
            for (let i = 0; i < formContainers.length; i++) {
                const item = formContainers[i];
                item.style.width = formStyles.inputs.width || defaultStyling.inputs.width;
                item.style.gap = formStyles.inputs.gap || defaultStyling.inputs.gap;
            }
        }

        //Form Input's Label Styling
        const inputLabels = document.getElementsByClassName('input-label');

        if(inputLabels){
            for (let i = 0; i < inputLabels.length; i++) {
                const label = inputLabels[i];
                label.style.fontWeight = formStyles.inputs.label.fontWeight || defaultStyling.inputs.fontWeight;
                label.style.fontSize = formStyles.inputs.label.fontSize || defaultStyling.inputs.fontSize;
                label.style.textDecoration = formStyles.inputs.label.textDecoration || defaultStyling.inputs.textDecoration;
                label.style.color = formStyles.inputs.label.fontColor || defaultStyling.inputs.label.fontColor;
            }
        }

        //Form Inputs Styling
        const formInputs = document.getElementsByClassName('form-item');

        if(formInputs){
            for (let i = 0; i < formInputs.length; i++) {
                const item = formInputs[i];

                item.style.width = formStyles.inputs.width || defaultStyling.inputs.width;
                item.style.height = formStyles.inputs.height || defaultStyling.inputs.height;
                item.style.padding = formStyles.inputs.padding || defaultStyling.inputs.padding;
                item.style.border = `${formStyles.inputs.borderWidth} ${formStyles.inputs.borderStyle} ${formStyles.inputs.borderColor}` || `${defaultStyling.inputs.borderWidth} ${defaultStyling.inputs.borderStyle} ${defaultStyling.inputs.borderColor}`;
                item.style.borderRadius = formStyles.inputs.borderRadius || defaultStyling.inputs.borderRadius;
                item.style.outlineColor = formStyles.inputs.focusBorderColor || defaultStyling.inputs.focusBorderColor;
                item.style.fontSize = formStyles.inputs.fontSize || defaultStyling.inputs.fontSize;
                item.style.color = formStyles.inputs.fontColor || defaultStyling.inputs.fontColor;
                item.style.transition = formStyles.inputs.transition || defaultStyling.inputs.transition;

                item.onmouseover = ()=>{
                    item.style.borderColor = formStyles.inputs.focusBorderColor || defaultStyling.inputs.focusBorderColor;
                }

                item.onmouseleave = ()=>{
                    item.style.borderColor = formStyles.inputs.borderColor || defaultStyling.inputs.borderColor;
                }
            }
        }

        //Form Submit Button Styling
        const submitButtons = document.querySelectorAll('.form-button');
        
        if(submitButtons){
            for (let i = 0; i < submitButtons.length; i++) {
                const buttons = submitButtons[i];
                buttons.style.width = formStyles.button.width || defaultStyling.button.width;
                buttons.style.height = formStyles.button.height || defaultStyling.button.height;
                buttons.style.padding = formStyles.button.padding || defaultStyling.button.padding;
                buttons.style.margin = formStyles.button.margin || defaultStyling.button.margin;
                buttons.style.border = `${formStyles.button.borderWidth} ${formStyles.button.borderStyle} ${formStyles.button.borderColor}` || `${defaultStyling.button.borderWidth} ${defaultStyling.button.borderStyle} ${defaultStyling.button.borderColor}`;
                buttons.style.borderRadius = formStyles.button.borderRadius || defaultStyling.button.borderRadius;
                buttons.style.backgroundColor = formStyles.button.backgroundColor || defaultStyling.button.backgroundColor;
                buttons.style.fontSize = formStyles.button.fontSize || defaultStyling.button.fontSize;
                buttons.style.color = formStyles.button.fontColor || defaultStyling.button.fontColor;
                buttons.style.textAlign = formStyles.button.textAlign || defaultStyling.button.textAlign;
                buttons.style.transition = formStyles.button.transition || defaultStyling.button.transition;

                buttons.onmouseover = ()=>{
                    buttons.style.backgroundColor = formStyles.button.hoverBackgroundColor || defaultStyling.button.hoverBackgroundColor;
                }

                buttons.onmouseleave = ()=>{
                    buttons.style.backgroundColor = formStyles.button.backgroundColor || defaultStyling.button.backgroundColor;
                }
            }
        }
    }

    //Function that returns an array of the key/values of each of the inputs
    const formatInputs = (formValues)=>{
        const formData = new FormData(formValues);
        let formattedInputs = [];

        for (const [k, v] of formData.entries()) {
            formattedInputs.push({name: k, value: v});
	    }

        return formattedInputs;
    }

    //Function called when form is submitted
    const formSubmitted = (e)=>{
        const formattedInputs = formatInputs(e.target);
        dispatch('formSubmitted', formattedInputs);
    }

</script>

<slot name="form-outter-top-slot"></slot>

<form class="modular-form" on:submit|preventDefault|stopPropagation={formSubmitted}>
    <!--Title texts for the form which only displays if a title is provided in the formOptions-->
    {#if formOptions.formTitle}
    <h1 class="form-title">{formOptions.formTitle}</h1>
    {/if}

    <slot name="form-inner-top-slot"></slot>

    <!--Each loop that add each of the specified inputs to the form, uses fallback info if property isn't specified-->
    {#each formOptions.formItems as item}
        <!--If the input is required a 'required' property is added-->
        {#if item.isRequired}
        <div class="input-container">
            {#if item.label}
            <label class="input-label" for={item.name || `form-item-${item.type || "text"}-${formOptions.formItems.indexOf(item)}`}>{item.label}</label>
            {/if}
            <input class="form-item" type={item.type || "text"} placeholder={item.placeholder || ""} name={item.name || `form-item-${item.type || "text"}-${formOptions.formItems.indexOf(item)}`} required>
        </div>
        {:else}
        <div class="input-container">
            {#if item.label}
            <label class="input-label" for={item.name || `form-item-${item.type || "text"}-${formOptions.formItems.indexOf(item)}`}>{item.label}</label>
            {/if}
            <input class="form-item" type={item.type || "text"} placeholder={item.placeholder || ""} name={item.name || `form-item-${item.type || "text"}-${formOptions.formItems.indexOf(item)}`}>
        </div>
        {/if}
    {/each}

    <slot name="form-inner-bottom-slot"></slot>

    <!--Submit button for the form, uses fallback data if properties aren't provided-->
    <button class="form-button" type="submit">{formOptions.submitButtonText || defaultOptions.submitText}</button>

    <slot name="form-inner-bottom-slot-two"></slot>
</form>

<slot name="form-outter-bottom-slot"></slot>

<style>
.modular-form{
    display: flex;
    flex-direction: column;
    user-select: none;
}

.input-container{
    display: flex;
    flex-direction: column;
}

.form-button{
    cursor: pointer;
}
</style>