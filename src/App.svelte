<script>
	import ModularForm from "./ModularForm.svelte";

	let formOptions = {
		formTitle: "Login",
		formItems: [
			{type: "text", placeholder: "Username", isRequired: true},
			{type: "password", placeholder: "Password", isRequired: true}
		]
	}

	let formStyles = {
        container: {
            width: "40%",
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
            width: "100%",
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

	const formSubmitted = (e)=>{
		const formInfo = e.detail;
		console.log(formInfo);
	}

</script>

<svelte:head>
	<title>Modular Form</title>
</svelte:head>

<main>
	<ModularForm on:formSubmitted={formSubmitted} bind:formOptions bind:formStyles/>
</main>

<style>
main{
	display: flex;
	justify-content: center;
	align-items: center;
}
</style>