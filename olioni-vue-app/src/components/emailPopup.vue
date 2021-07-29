<template>
    <div class="container" :style="{backgroundColor: bgClr}">
        <form @submit.prevent="submitEmail()">
            <div v-if="confirmed" class="tyWrap">
                <h2 class="tyText" @mouseover="hover()" @mouseout="unhover()"> {{ tyText }} </h2>
            </div>
            <div v-if="confirming" class="inputsWrap">
                <div class="inputContainer">
                    <h2 class="inputHeader">PARENT EMAIL ADRRESS</h2>
                    <input>
                </div>
                <div class="inputContainer">
                    <h2 class="inputHeader">TEACHER EMAIL ADRRESS</h2>
                    <input>
                </div>
            </div>
            <div v-if="confirming" class="buttonWrap">
                <button class="confirmButton" @click="confirmEmails(), rng()">CONFIRM</button>
            </div>
        </form>
    </div>
</template>

<script>
import{ init } from 'emailjs-com';
init("user_9ldq54a73yTROgi8azUq4");

export default ({
    name: 'emailPopup',
    props: [],
    data() {
        return {
            confirming: true,
            confirmed: false,

            bgClr: '#7c4ebf',
            tyText: 'Thank you for your input 👍'
        }
    },
    methods: {
        confirmEmails() {
            this.confirming = false
            this.confirmed = true
        },
        rng() {
            this.bgClr = '#5bc7ac'
        },
        hover() {
            this.tyText = '✨ Thank you for your input ✨'
        },
        unhover() {
            this.tyText = 'Thank you for your input 👍'
        },
        sendEmail: (e) => {
            emailjs.sendForm('service_16lidpm', 'template_2h8mbw5', e.target, 'user_9ldq54a73yTROgi8azUq4')
                .then((result) => {
                    console.log('SUCCESS!', result.status, result.text);
                }, (error) => {
                    console.log('FAILED...', error);
                });
            }
    }
})
</script>

<style scoped>

* {
    margin: 0;
}

.container {
    display: flex;
    position: absolute;

    width: 100vw;
    height: 100vh;

    justify-content: center;
    align-items: center;

    background-color: #1e6ae3;

    flex-direction: column;

    transition: 0.6s;
}

.inputsWrap {
    width: 100vw;
    height: 50vh;

    transition: 0.6s;
}

.inputContainer {
    height: 20vh;
}

.inputHeader {
    margin-bottom: 2vh;
    color: black;
}

.confirmButton {
  width: 80vw;
  height: 10vh;
  
  background-color: white;

  border: none;
  border-radius: 10px;
  
  transition: 0.3s;
}

.confirmButton:hover {
  cursor: pointer;
  font-size: 20px;

  background-color: rgb(238, 238, 238);
}

input {
    width: 60vw;
    height: 6vh;

    border: none;

    border-radius: 5px;

    font-size: 18px;

    text-align: center;
}

.tyWrap {
    width: 100vw;
    height: 100vh;
    
    display: flex;
    justify-content: center;
    align-items: center;

    color: white;

    font-size: 25px;

    transition: 0.6s;
}

.tyText {
    transition: 0.3s;
}
</style>