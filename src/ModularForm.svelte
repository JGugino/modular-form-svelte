<script>
    import { onMount, createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

    export let formOptions = {
        formTitle: "Register",
        formItems: [
            {type: "text", label: "Username", isRequired: true},
            {type: "email", label: "Email", isRequired: true},
            {type: "password", label: "Password", isRequired: true},
            {type: "password", label: "Confirm Password", isRequired: true}
        ],
        submitButtonText: "Submit"
    }

    export let formStyles = {
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
            transition: 'border-color ease-in-out 200ms, background-color ease-in-out 200ms, outline ease-in-out 200ms'
        }
    }

    //Default Form Styling
    const defaultWidth = '10rem';
    const defaultPadding = '1em';
    const defaultMargin = '1rem';
    const defaultGap = '1rem';
    const defaultBorder = '1px solid black';
    const defaultBorderRadius = '10px';
    const defaultBackgroundColor = '#ffffff';

    //Default Input Styling
    const defaultInputGap = '0.6rem';

    onMount(()=>{
        applyStyles();
    });

    const applyStyles = ()=>{
        const modularForm = document.querySelector('.modular-form');

        //Main Form Styling
        modularForm.style.width = formStyles.container.width || defaultWidth;
        modularForm.style.padding = formStyles.container.padding || defaultPadding;
        modularForm.style.margin = formStyles.container.margin || defaultMargin;
        modularForm.style.gap = formStyles.container.gap || defaultGap;
        modularForm.style.border = `${formStyles.container.borderWidth} ${formStyles.container.borderStyle} ${formStyles.container.borderColor}` || defaultBorder;
        modularForm.style.borderRadius = formStyles.container.borderRadius || defaultBorderRadius;
        modularForm.style.backgroundColor = formStyles.container.backgroundColor || defaultBackgroundColor;
    
        //Input Containers Styling
        const formContainers = document.getElementsByClassName('input-container');

        for (let i = 0; i < formContainers.length; i++) {
            const item = formContainers[i];
            item.style.width = formStyles.container.width || defaultWidth;
            item.style.gap = formStyles.inputs.gap || defaultInputGap;
        }

        //Form Inputs Styling
        const formInputs = document.getElementsByClassName('form-item');

        for (let i = 0; i < formInputs.length; i++) {
            const item = formInputs[i];

            item.style.width = formStyles.inputs.width;
            item.style.height = formStyles.inputs.height;
            item.style.padding = formStyles.inputs.padding;
            item.style.border = `${formStyles.inputs.borderWidth} ${formStyles.inputs.borderStyle} ${formStyles.inputs.borderColor}`;
            item.style.borderRadius = formStyles.inputs.borderRadius;
            item.style.outlineColor = formStyles.inputs.focusBorderColor;
            item.style.fontSize = formStyles.inputs.fontSize;
            item.style.transition = formStyles.inputs.transition;

            item.onmouseover = ()=>{
                item.style.borderColor = formStyles.inputs.focusBorderColor;
            }

            item.onmouseleave = ()=>{
                item.style.borderColor = formStyles.inputs.borderColor;
            }
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
    {#each formOptions.formItems as item}
        {#if item.isRequired}
        <div class="input-container">
            {#if item.label}
            <label for={item.name || `form-item-${item.type || "text"}-${formOptions.formItems.indexOf(item)}`}>{item.label}</label>
            {/if}
            <input class="form-item" type={item.type || "text"} placeholder={item.placeholder || ""} name={item.name || `form-item-${item.type || "text"}-${formOptions.formItems.indexOf(item)}`} required>
        </div>
        {:else}
        <div class="input-container">
            {#if item.label}
            <label for={item.name || `form-item-${item.type || "text"}-${formOptions.formItems.indexOf(item)}`}>{item.label}</label>
            {/if}
            <input class="form-item" type={item.type || "text"} placeholder={item.placeholder || ""} name={item.name || `form-item-${item.type || "text"}-${formOptions.formItems.indexOf(item)}`}>
        </div>
        {/if}
    {/each}


    <button class="form-button" type="submit">{formOptions.submitButtonText}</button>
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

</style>