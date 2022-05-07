<script>
	import ModularForm from "./ModularForm.svelte";

	const formSubmitted = (e)=>{
		const formInfo = e.detail;
		console.log(formInfo);
	}

</script>

<svelte:head>
	<title>Modular Form</title>
</svelte:head>

<main>
	<ModularForm on:formSubmitted={formSubmitted}/>
</main>

<style>
main{
	display: flex;
	justify-content: center;
	align-items: center;
}
</style>