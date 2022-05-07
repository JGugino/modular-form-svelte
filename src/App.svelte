<script>
	import ModularForm from "./ModularForm.svelte";

	let formOptions = {
		formTitle: "Login",
		formItems: [
			{type: "text", placeholder: "Username", isRequired: true},
			{type: "password", placeholder: "Password", isRequired: true}
		]
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
	<ModularForm on:formSubmitted={formSubmitted} bind:formOptions={formOptions}/>
</main>

<style>
main{
	display: flex;
	justify-content: center;
	align-items: center;
}
</style>