<template>
    <div class="pageContainer">

        <div class="loginContainer">
            <div class="p-1 w-100">
                <div>
                    <h1 class="loginTitle">Se connecter</h1>
                </div>


                <div id="logoContainer">
                    <div id="logo"></div>
                </div>

                <div>
                    <!-- Input velden voor in te loggen (bootstrap) -->
                    <!-- En voor de icons https://primevue.org/icons/ -->
                    <div class="input-group mb-3 ">
                        <span class="input-group-text" id="basic-addon1"><span class="pi pi-user text-dark"></span></span>
                        <input v-model="email" type="text" class="form-control" placeholder="E-mail"  aria-label="email"
                            aria-describedby="basic-addon1">
                    </div>
                    <!-- Input velden voor in te loggen (bootstrap) -->
                    <div class="input-group mb-3">
                        <span class="input-group-text" id="basic-addon1"><span class="pi pi-key text-dark"></span></span>
                        <input v-model="password" ref="inputType" type="password" class="form-control" placeholder="Mot de passe"
                            aria-label="paswoord" aria-describedby="basic-addon1">
                        <span class="input-group-text" id="basic-addon1"><span @click="changeInputType(inputType, eyeIcon)" ref="eyeIcon"
                                class="pi pi-eye-slash text-dark" id="togglePassword" role="button"></span></span>
                    </div>


                    <div class="d-grid gap-2">
                        <button class="btn btn-light  border border-light" type="button" @click="auth(email, password)">Se
                            connecter</button>
                    </div>


                    <div class="d-flex justify-content-between">
                        <a class="btn btn-link p-lg-0  text-white txtAccount" href="/register">Vous n'avez
                            pas de compte ?</a>
                        <a class="btn btn-link p-lg-0  text-white txtPwd" href="/recover">Mot de passe
                            oublié ?</a>
                    </div>
                </div>
            </div>

        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
const router = useRouter(); // router om te navigeren //
const inputType = ref(); // ref voor het type van het input veld //
const eyeIcon = ref(); // ref voor het eye icon te veranderen //

const email = ref(''); // ref voor het email veld //
const password = ref(''); // ref voor het password veld //

function changeInputType(input, icon) {
    if (input.type == 'password') {
        input.type = 'text';
        icon.classList.remove('pi-eye-slash');
        icon.classList.add('pi-eye');
    } else {
        input.type = 'password';
        icon.classList.remove('pi-eye');
        icon.classList.add('pi-eye-slash');
    }
}

 // DUS LATER IN DE STORE(ik laat die hier om visu te hebben) //
function auth(inputEmail, inputPassword) {  // DEZE METHODE MOET IN DE STORE GEIMPLEMENTEERD WORDEN IMO //
    console.log(inputEmail, ", ", inputPassword);
    router.push('/home');
}

</script>

<style scoped>
.pageContainer {
    height: 100vh;
    width: 100vw;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0px;
    background-color: #181818;
}

.loginContainer {
    background-color:#0D6EFD;
    border-radius: 25px;
    border: solid 1px rgb(255, 255, 255);
    padding: 25px;
    width: 450px;
    /* min-width: 300px; */
}


.loginTitle {
    text-align: center;
    color: white;
    
}

#logoContainer {
    display: flex;
    justify-content: center;
}

#logo {
    padding: 50px;
    background-image: url(/src/assets/friends-icon.png);
    filter: invert(97%) sepia(0%) saturate(2%) hue-rotate(112deg) brightness(118%) contrast(100%);
    opacity: 0.6;
    background-size: contain;
    background-repeat: no-repeat;
}

.form-control {
    font-family: 'Courier New', Courier, monospace;
}

.txtInput {
    display: block;
    border-radius: 5px;
    font-size: 16px;
    background: white;
    width: 100%;
    border: 0;
    padding: 10px 10px;
    margin: 15px;
}

*:focus {
    box-shadow: none !important;
}

.bloc {
    padding: 5px;
    background-color: #ffffff;
}

@media only screen and (max-width: 420px) {

    .txtAccount,
    .txtPwd {
        font-size: small;
    }

   .pageContainer {
    display: block;
   }
   .loginContainer {
    width: 100%;
    border-radius: 0px;
    padding: 15px;
    padding-top: 25px;
   }
}
</style>