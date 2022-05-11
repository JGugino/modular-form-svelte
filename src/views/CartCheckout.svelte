<script>
    import ModularForm from "../ModularForm.svelte";

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

    let formStyles = {
        container: {
            width: "40rem",
            padding: "1em 2em",
            margin: "0",
            gap: "1rem",
            borderColor: "#79DAE8",
            borderWidth: "1px",
            borderStyle: "solid",
            borderRadius: "10px",
            backgroundColor: "#E8F9FD",
            fontFamily: "'Overpass', sans-serif"
        },
        title:{
            fontSize: "32pt",
            margin: "0.4rem auto",
            padding: "0",
            fontWeight: "bold",
            fontColor: "#62929e",
            textDecoration: "none",
        },
        inputs:{
            width: "100%",
            height: "3rem",
            padding: "0.4em 0.8em 0.4em 0.8em",
            margin: "0rem",
            gap: "0.6rem",
            fontSize: '14pt',
            fontColor: "black",
            borderColor: "#0AA1DD",
            borderWidth: "1px",
            borderStyle: "solid",
            borderRadius: "10px",
            backgroundColor: "#E8F9FD",
            hoverBackgroundColor: "#dbdbdb",
            focusBorderColor: '#0AA1DD',
            transition: 'border-color ease-in-out 200ms, background-color ease-in-out 200ms, outline ease-in-out 200ms',
            label:{
                fontSize: '14pt',
                fontWeight: 'normal',
                textDecoration: 'none',
                fontColor: "#fdfdff",
            }
        },
        button:{
            width: "60%",
            height: "3rem",
            padding: "0",
            margin: "0 auto",
            fontSize: "16pt",
            fontColor: "black",
            textAlign: "center",
            borderColor: "#0AA1DD",
            borderWidth: "1px",
            borderStyle: "solid",
            borderRadius: "10px",
            backgroundColor: "#79DAE8",
            hoverBackgroundColor: "#54d1e3",
            transition: 'border-color ease-in-out 200ms, background-color ease-in-out 200ms, outline ease-in-out 200ms'
        }
    }

    const formSubmitted = (e)=>{
        const formInfo = e.detail;
        console.log(formInfo);
    }
</script>

<div id="cart-checkout">
    <header>
        <h1>Expression Electronics</h1>
        <ul>
            <li>Home</li>
            <li>Shop</li>
            <li>Account</li>
        </ul>
    </header>

    <div class="cart-view">
        <h2>Cart</h2>
        <div class="cart-item">
            <img src="./assets/monitor.jpg" alt="Cart Item Icon">
            <p>XtraWide 1440p GAMING Monitor</p>
            <p>$400</p>
        </div>
        <div class="cart-item">
            <img src="./assets/chair.jpg" alt="Cart Item Icon">
            <p>Super Comfortable GAMING Chair</p>
            <p>$400</p>
        </div>
    </div>

    <hr class="middle-hr">

    <div class="checkout-info">
        <ModularForm bind:formOptions bind:formStyles on:formSubmitted={formSubmitted}>
        <div slot="form-inner-bottom-slot" class="inner-slot">
            <hr>
            <input type="text" placeholder="Name on Card" required class="form-item">
            <input type="text" placeholder="Card Number" required class="form-item">
            <div class="card-info">
                <input type="text" placeholder="Exp. Date" required class="form-item">
                <input type="text" placeholder="Security Code" required class="form-item">
            </div>
        </div>    
        </ModularForm>
        <div class="checkout-amount">
            <div class="amount-item">
                <p>Subtotal:</p> <p>$800</p>
            </div>
            <div class="amount-item">
                <p>Tax:</p> <p>$20</p>
            </div>
            <div class="amount-item total">
                <p>Total:</p> <p>$820</p>
            </div>
        </div>
    </div>

    <footer>
        &copy; Expression Electronics 2022, All rights reserved.
    </footer>
</div>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Overpass:wght@300;400;500;600;700&display=swap');

    #cart-checkout{
        width: 100%;
        background-color: #ffffff;
        font-family: 'Overpass', sans-serif;
    }

    .cart-view{
        display: flex;
        flex-direction: column;
        gap: 1rem;
        margin: 1.4rem 0;
        text-align: center;
    }

    .cart-view > h2{
        font-size: 28pt;
        text-decoration: underline;
        user-select: none;
    }

    .cart-item{
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 0.8em 1.8em;
        margin: 0.8rem 2rem;
        font-size: 16pt;
        background-color: #E8F9FD;
        border: 1px solid #79DAE8;
        border-radius: 10px;
    }

    .cart-item > img{
        width: 120px;
        background-color: #ffffff;
        padding: 0.4em;
        border-radius: 10px;
    }

    .checkout-info{
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        gap: 4rem;
    }

    .checkout-amount{
        display: flex;
        flex-direction: column;
        gap: 1.2rem;
        width: 20rem;
        height: 14rem;
        padding: 2em;
        font-size: 16pt;
        background-color: #E8F9FD;
        border-radius: 10px;
        border: 1px solid #79DAE8;
        user-select: none;
    }

    .card-info{
        display: flex;
        gap: 1rem;
    }

    .amount-item{
        display: flex;
        justify-content: space-between;
    }

    .total{
        font-weight: bold;
        color: #2155CD;
    }

    .middle-hr{
        margin: 1.8rem auto;
        width: 60%;
        outline: none;
        border: 1px solid #0AA1DD;
    }

    .inner-slot{
        display: flex;
        flex-direction: column;
        gap: 1rem;
    }

    .inner-slot > hr{
        width: 80%;
        margin: 0 auto;
        outline: none;
        border: 1px solid #0AA1DD;
    }

    header{
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1em 12em 1em 4em;
        margin-bottom: 4rem;
        height: 8rem;
        user-select: none;
        background-color: #2155CD;
    }

    header h1{
        font-size: 38pt;
        color: #E8F9FD;
    }

    header > ul{
        display: flex;
        gap: 4rem;
        list-style: none;
        font-size: 18pt;
    }

    header > ul > li{
        color: #E8F9FD;
        cursor: pointer;
        transition: color ease-in-out 200ms;
    }

    header > ul > li:hover{
        color: #79DAE8;
    }

    footer{
        text-align: center;
        margin: 1rem 0;
        font-size: 10pt;
        user-select: none;
    }
</style>