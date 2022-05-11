<script>
    import AccountCreate from "./views/AccountCreate.svelte";
    import CartCheckout from './views/CartCheckout.svelte'

    const possibleViews = ['account', 'checkout'];
    let currentView = possibleViews[1];


    import ModularForm from "./ModularForm.svelte";

    let formOptions = {
        formItems: [
            {type: "text", name: "checkout-name", placeholder: "Full Name", isRequired: true},
            {type: "text", name: "checkout-email", placeholder: "Email", isRequired: true},
            {type: "text", name: "checkout-address", placeholder: "Address", isRequired: true},          
            {type: "text", name: "checkout-city", placeholder: "City", isRequired: true},          
            {type: "text", name: "checkout-state", placeholder: "State", isRequired: true},          
            {type: "text", name: "checkout-zipcode", placeholder: "ZipCode", isRequired: true},          
        ],
        submitButtonText: "Checkout"
    }

</script>

<svelte:head>
	<title>Modular Form</title>
</svelte:head>

<main>
    {#if currentView == possibleViews[0]}
    <AccountCreate />
    {:else if currentView == possibleViews[1]}
    <CartCheckout />
    {:else}
        <ModularForm bind:formOptions/>
    {/if}
</main>

<style>
main{
	display: flex;
	justify-content: center;
	align-items: center;
    width: 100%;
}
</style>