<script>
    import { onMount, createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

    //Default options and styling for the form
    const defaultOptions = {
        title: "Example",
        items: [
            {type: "text", label: "Name", isRequired: true},
            {type: "email", label: "Email", isRequired: true},
            {type: "date", label: "Date of Birth", isRequired: true},
        ],
        submitText: "Submit"
    }

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
            textDecoration: "none",
        },
        inputs:{
            width: "22rem",
            height: "3rem",
            padding: "0.4em 0 0.4 1.4em",
            margin: "0rem",
            gap: "0.6rem",
            fontSize: '14pt',
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
            }
        },
        button:{
            width: "10rem",
            height: "3rem",
            padding: "0",
            margin: "0 auto",
            fontSize: "16pt",
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

    export let formOptions = {
        formTitle: defaultOptions.title,
        formItems: defaultOptions.items,
        submitButtonText: defaultOptions.submitText,
    }

    export let formStyles = defaultStyling;

    onMount(()=>{
        applyStyles();
    });

    const applyStyles = ()=>{
        const modularForm = document.querySelector('.modular-form');

        //Main Form Styling
        modularForm.style.width = formStyles.container.width || defaultStyling.container.width;
        modularForm.style.padding = formStyles.container.padding || defaultStyling.container.padding;
        modularForm.style.margin = formStyles.container.margin || defaultStyling.container.margin;
        modularForm.style.gap = formStyles.container.gap || defaultStyling.container.gap;
        modularForm.style.border = `${formStyles.container.borderWidth} ${formStyles.container.borderStyle} ${formStyles.container.borderColor}` || `${defaultStyling.container.borderWidth} ${defaultStyling.container.borderStyle} ${defaultStyling.container.borderColor}`;
        modularForm.style.borderRadius = formStyles.container.borderRadius || defaultStyling.container.borderRadius;
        modularForm.style.backgroundColor = formStyles.container.backgroundColor || defaultStyling.container.backgroundColor;
    

        //Form Title Styling
        const formTitle = document.querySelector('.form-title');

        formTitle.style.fontSize = formStyles.title.fontSize || defaultStyling.title.fontSize;
        formTitle.style.textDecoration = formStyles.title.textDecoration || defaultStyling.title.textDecoration;;
        formTitle.style.margin = formStyles.title.margin || defaultStyling.title.margin;;
        formTitle.style.padding = formStyles.title.padding || defaultStyling.title.padding;;
        formTitle.style.fontWeight = formStyles.title.fontWeight || defaultStyling.title.fontWeight;

        //Input Containers Styling
        const formContainers = document.getElementsByClassName('input-container');

        for (let i = 0; i < formContainers.length; i++) {
            const item = formContainers[i];
            item.style.width = formStyles.container.width || defaultStyling.container.width;
            item.style.gap = formStyles.inputs.gap || defaultStyling.inputs.gap;
        }

        //Form Input's Label Styling
        const inputLabels = document.getElementsByClassName('input-label');

        for (let i = 0; i < inputLabels.length; i++) {
            const label = inputLabels[i];
            label.style.fontWeight = formStyles.inputs.label.fontWeight || defaultStyling.inputs.fontWeight;
            label.style.fontSize = formStyles.inputs.label.fontSize || defaultStyling.inputs.fontSize;
            label.style.textDecoration = formStyles.inputs.label.textDecoration || defaultStyling.inputs.textDecoration;
        }

        //Form Inputs Styling
        const formInputs = document.getElementsByClassName('form-item');

        for (let i = 0; i < formInputs.length; i++) {
            const item = formInputs[i];

            item.style.width = formStyles.inputs.width || defaultStyling.inputs.width;
            item.style.height = formStyles.inputs.height || defaultStyling.inputs.height;
            item.style.padding = formStyles.inputs.padding || defaultStyling.inputs.padding;
            item.style.border = `${formStyles.inputs.borderWidth} ${formStyles.inputs.borderStyle} ${formStyles.inputs.borderColor}` || `${defaultStyling.inputs.borderWidth} ${defaultStyling.inputs.borderStyle} ${defaultStyling.inputs.borderColor}`;
            item.style.borderRadius = formStyles.inputs.borderRadius || defaultStyling.inputs.borderRadius;
            item.style.outlineColor = formStyles.inputs.focusBorderColor || defaultStyling.inputs.focusBorderColor;
            item.style.fontSize = formStyles.inputs.fontSize || defaultStyling.inputs.fontSize;
            item.style.transition = formStyles.inputs.transition || defaultStyling.inputs.transition;

            item.onmouseover = ()=>{
                item.style.borderColor = formStyles.inputs.focusBorderColor || defaultStyling.inputs.focusBorderColor;
            }

            item.onmouseleave = ()=>{
                item.style.borderColor = formStyles.inputs.borderColor || defaultStyling.inputs.borderColor;
            }
        }

        //Form Submit Button Styling
        const submitButton = document.querySelector('.form-button');
        
        submitButton.style.width = formStyles.button.width || defaultStyling.button.width;
        submitButton.style.height = formStyles.button.height || defaultStyling.button.height;
        submitButton.style.padding = formStyles.button.padding || defaultStyling.button.padding;
        submitButton.style.margin = formStyles.button.margin || defaultStyling.button.margin;
        submitButton.style.border = `${formStyles.button.borderWidth} ${formStyles.button.borderStyle} ${formStyles.button.borderColor}` || `${defaultStyling.button.borderWidth} ${defaultStyling.button.borderStyle} ${defaultStyling.button.borderColor}`;
        submitButton.style.borderRadius = formStyles.button.borderRadius || defaultStyling.button.borderRadius;
        submitButton.style.backgroundColor = formStyles.button.backgroundColor || defaultStyling.button.backgroundColor;
        submitButton.style.fontSize = formStyles.button.fontSize || defaultStyling.button.fontSize;
        submitButton.style.textAlign = formStyles.button.textAlign || defaultStyling.button.textAlign;
        submitButton.style.transition = formStyles.button.transition || defaultStyling.button.transition;

        submitButton.onmouseover = ()=>{
            submitButton.style.backgroundColor = formStyles.button.hoverBackgroundColor || defaultStyling.button.hoverBackgroundColor;
        }

        submitButton.onmouseleave = ()=>{
            submitButton.style.backgroundColor = formStyles.button.backgroundColor || defaultStyling.button.backgroundColor;
        }
    }

    const formatInputs = (formValues)=>{
        const formData = new FormData(formValues);
        let formattedInputs = [];

        for (const [k, v] of formData.entries()) {
            formattedInputs.push({name: k, value: v});
	    }

        return formattedInputs;
    }

    const formSubmitted = (e)=>{
        const formattedInputs = formatInputs(e.target);
        dispatch('formSubmitted', formattedInputs);
    }

</script>

<form class="modular-form" on:submit|preventDefault|stopPropagation={formSubmitted}>
    {#if formOptions.formTitle}
    <h1 class="form-title">{formOptions.formTitle}</h1>
    {/if}

    <slot name="form-top-slot"></slot>

    {#each formOptions.formItems as item}
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

    <button class="form-button" type="submit">{formOptions.submitButtonText || defaultOptions.submitText}</button>

    <slot name="form-bottom-slot"></slot>
</form>

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