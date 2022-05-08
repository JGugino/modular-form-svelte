<script>
    import AccountCreate from "./views/AccountCreate.svelte";

    const possibleViews = ['account', 'contact', 'checkout'];
    let currentView = possibleViews[0];
</script>

<svelte:head>
	<title>Modular Form</title>
</svelte:head>

<main>
    {#if currentView == possibleViews[0]}
    <AccountCreate />
    {:else if currentView == possibleViews[1]}
    <h1>Contact</h1>
    {:else if currentView == possibleViews[3]}
    <h1>Checkout</h1>
    {/if}
</main>

<style>
main{
	display: flex;
	justify-content: center;
	align-items: center;
}
</style>