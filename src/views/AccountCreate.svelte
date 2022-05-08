<script>
	import ModularForm from "../ModularForm.svelte";

    let showLogin = true;

    let loginFormOptions = {
        formTitle: "Login",
        formItems: [
            {type: "text", name: "login-username", label: "Username: ", isRequired: true},
            {type: "password", name: "login-password", label: "Password: ", isRequired: true}
        ],
        submitButtonText: "Login"
    }

    let registerFormOptions = {
        formTitle: "Register",
        formItems: [
            {type: "text", name: "register-username", label: "Username: ", isRequired: true},
            {type: "email", name: "register-email", label: "Email: ", isRequired: true},
            {type: "date", name: "register-date", label: "Date of Birth: ", isRequired: true},
            {type: "password", name: "register-password", label: "Password: ", isRequired: true},
            {type: "password", name: "register-password-confirm", label: "Confirm Password: ", isRequired: true}
        ],
        submitButtonText: "Register"
    }

    let formStyles = {
        container: {
            width: "26%",
            padding: "1em 2em",
            margin: "1rem 0",
            gap: "1rem",
            borderColor: "#62929e",
            borderWidth: "1px",
            borderStyle: "solid",
            borderRadius: "10px",
            backgroundColor: "#393d3f"
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
            focusBorderColor: '#546a7b',
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
            borderColor: "#62929e",
            borderWidth: "1px",
            borderStyle: "solid",
            borderRadius: "10px",
            backgroundColor: "#ffffff",
            hoverBackgroundColor: "#c6c5b9",
            transition: 'border-color ease-in-out 200ms, background-color ease-in-out 200ms, outline ease-in-out 200ms'
        }
    }

    const formSubmitted = (e, id)=>{
        const formInfo = e.detail;

        switch(id){
            case 0:
                console.log('Login:');
                console.log(formInfo);
                break;

            case 1:
                console.log('Register:');
                console.log(formInfo);
                break;
        }
    }
</script>

<div id="account-create">
    <header>
        <h1>TechZen</h1>
    </header>

    <div class="forms">
        {#if showLogin}
        <ModularForm on:formSubmitted={(e)=>{formSubmitted(e, 0)}} bind:formOptions={loginFormOptions} bind:formStyles>
            <div slot="form-inner-bottom-slot-two">
                <div class="social-media-buttons">
                    <div class="custom-button">
                        <svg width="48" height="48" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M24 17.6213C25.9529 17.6213 27.2702 18.4649 28.0214 19.1698L30.9565 16.304C29.1538 14.6284 26.808 13.6 24 13.6C19.9325 13.6 16.4196 15.9342 14.7094 19.3315L18.072 21.9431C18.9156 19.4355 21.2498 17.6213 24 17.6213Z" fill="#EA4335"/>
                            <path d="M33.984 24.2311C33.984 23.376 33.9147 22.752 33.7644 22.1049H24V25.9644H29.7316C29.616 26.9235 28.992 28.368 27.6053 29.3386L30.8871 31.8809C32.8516 30.0666 33.984 27.3973 33.984 24.2311Z" fill="#4285F4"/>
                            <path d="M18.0836 26.0569C17.864 25.4098 17.7369 24.7164 17.7369 24C17.7369 23.2835 17.864 22.5902 18.072 21.9431L14.7093 19.3315C14.0045 20.7413 13.6 22.3244 13.6 24C13.6 25.6755 14.0045 27.2587 14.7093 28.6684L18.0836 26.0569Z" fill="#FBBC05"/>
                            <path d="M24 34.4C26.808 34.4 29.1653 33.4756 30.8871 31.8809L27.6053 29.3387C26.7271 29.9511 25.5484 30.3787 24 30.3787C21.2498 30.3787 18.9156 28.5644 18.0836 26.0569L14.7209 28.6684C16.4311 32.0658 19.9324 34.4 24 34.4Z" fill="#34A853"/>
                            </svg>
                            <button class="alt-login-button google" on:click|preventDefault={()=>{console.log('Google Login')}}>Login with Google</button>
                    </div>
                    <button class="alt-login-button facebook" on:click|preventDefault={()=>{console.log('Facebook Login')}}>Login with Facebook</button>
                </div>
                <p class="help-text">Need an account? <a on:click|preventDefault={()=>{showLogin = false;}} href="#register">Register here!</a></p>
            </div>
        </ModularForm>
        {:else}
        <ModularForm on:formSubmitted={(e)=>{formSubmitted(e, 1)}} bind:formOptions={registerFormOptions} bind:formStyles>
            <div slot="form-inner-bottom-slot-two">
                <p class="help-text">Already have an account? <a on:click|preventDefault={()=>{showLogin = true;}} href="#login">Login here!</a></p>
            </div>
        </ModularForm>
        {/if}
    </div>

    <footer>
        &copy; Copyright TechZen 2022, All rights reserved.
    </footer>
</div>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Nunito:ital,wght@0,300;0,400;0,500;1,500&display=swap');

    #account-create{
        display: flex;
        width: 100%;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        font-family: 'Nunito', sans-serif;
        background-color: #fdfdff;
   }

   header{
       width: 100%;
       font-size: 32pt;
       background-color: #393d3f;
       user-select: none;
       text-align: center;
       padding: 1em 0;
       color: #62929e;
   }

   .forms{
       display: flex;
       width: 100%;
       flex-direction: column;
       justify-content: center;
       align-items: center;
       margin: 1.8
       rem 0;
   }

   .social-media-buttons{
       display: flex;
       justify-content: center;
       align-items: center;
       gap: 1rem;
   }

   .alt-login-button{
        width: 80%;
        height: 3rem;
        padding: 0;
        margin: 0 auto;
        font-size: 12pt;
        color: black;
        text-align: center;
        border-color: #62929e;
        border-width: 1px;
        border-style: solid;
        border-radius: 10px;
        background-color: #ffffff;
        cursor: pointer;
        transition: background-color ease-in-out 200ms;
   }

   .facebook{
        color: #ffffff;
        background-color: rgb(22, 22, 227);
        border-color: rgb(14, 14, 187);
   }

   .facebook:hover{
        background-color: rgb(20, 20, 177);
   }

   .google{
       padding: 0 0 0 1.4em;
       width: 100%;
   }

   .custom-button{
       position: relative;
       width: 80%;
   }

   .custom-button svg{
       position: absolute;
       left: -0.2rem;
   }

   .help-text{
       text-align: center;
       color: #fdfdff;
       font-size: 14pt;
       margin: 1rem 0;
   }

   .help-text > a{
       text-decoration: none;
       color: #62929e;
       transition: color ease-in-out 200ms;
   }

   .help-text > a:hover{
        color: #60b4c9;
   }

   footer{
       user-select: none;
       margin: 1rem 0;
   }
</style>