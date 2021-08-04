<template>
    <div>
        <button
            class="button button-popup"
            @click="openPopUp"
        >
            К покупкам
        </button>
        <div
            v-if="showPopUp"
            class="popup-container"
        >
            <div class="popup">
                <img
                    class="cross"
                    src="/images/cross.svg"
                    alt=""
                    @click="closePopUp"
                >
                <input
                    class="input"
                    type="email"
                    v-model="email"
                    placeholder="Введите свой email"
                >
                <button
                    class="button button-email"
                    :disabled="!emailIsValid || sendingToServer"
                    @click="sendEmail"
                >
                    Отправить
                </button>
                <div class="p-rel">
                    <p
                        v-if="showMessage"
                        class="popup-message text-green"
                    >
                        Спасибо!
                    </p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                showPopUp: false,
                email: '',
                sendingToServer: false,
                showMessage: false
            }
        },
        methods: {
            openPopUp() {
                this.showPopUp = true;
                document.querySelector('html').style.overflowY = 'hidden'; // Залочивание экрана
            },
            closePopUp() {
                this.showPopUp = false;
                this.email = '';
                document.querySelector('html').style.overflowY = 'auto'; // Разлочивание экрана
            },
            sendEmail() {
                // Имитация связи с сервером
                this.sendingToServer = true;
                setTimeout(() => {
                    console.log(this.email);
                    this.sendingToServer = false;
                    this.showMessage = true;
                    setTimeout(() => {
                        this.showMessage = false;
                    }, 3000);
                }, 1500);
            }
        },
        computed: {
            emailIsValid() {
                // Регулярное выражение для эл. почты
                const reg = /^(([^<>()\[\]\.,;:\s@\"]+(\.[^<>()\[\]\.,;:\s@\"]+)*)|(\".+\"))@(([^<>()[\]\.,;:\s@\"]+\.)+[^<>()[\]\.,;:\s@\"]{2,})$/i;
                return reg.test(this.email)
            }
        }
    }
</script>

<style lang="scss" scoped>
    .button {
        background-color: #7db945;
        color: #fff;
        border: none;
        display: block;
        cursor: pointer;
        margin: auto;
    }
    .button-popup {
        border-radius: 10px;
        font-size: 22px;
        line-height: 36px;
        padding-top: 17px;
        padding-bottom: 17px;
    }
    .popup-container {
        position: fixed;
        top: 0;
        left: 0;
        width: 100vw;
        padding: 0 20px;
        box-sizing: border-box;
        height: 100vh;
        background-color: rgba(0, 0, 0, 0.4);
        display: flex;
        align-items: center;
        justify-content: center;
        .popup {
            max-width: 500px;
            width: 100%;
            padding: 30px;
            box-sizing: border-box;
            border: 1px solid #000;
            background-color: #fff;
            border-radius: 10px;
            position: relative;
            * {
                
                display: block;
            }
            .cross {
                margin-left: auto;
                width: 50px;
                cursor: pointer;
                position: relative;
                left: 25px;
                bottom: 25px;
            }
            .input {
                width: 100%;
                border: 1px solid #000;
                box-sizing: border-box;
                padding: 5px;
                border-radius: 2px;
                outline: none;
                margin-bottom: 20px;
                font-family: 'RotondaC';
            }
            .button-email {
                border-radius: 2px;
                max-width: 150px;
                width: 100%;
                padding: 10px;
            }
            .button-email:disabled {
                background-color: #6e6e6e;
                cursor: default;
            }
            .popup-message {
                position: absolute;
                text-align: center;
                width: 100%;
                margin-top: 7px;
            }
        }
    }
       // Tablet and desktop
    @media (min-width: 1024px) {
        .button-popup {
            padding-left: 110px;
            padding-right: 110px;
            margin-top: 50px;
        }
        .popup-container {
            font-size: 16px;
        }
    }
// Desktop
    @media (min-width: 1440px) {
        
    }
// Tablet
    @media (min-width: 1024px) and (max-width: 1439px) {
        
    }
// Mobile
    @media (max-width: 1023px) {
        .button-popup {
            margin-top: 31px;
            max-width: 390px;
            width: 100%;
            text-align: center;
        }
        .popup-container {
            font-size: 14px;
        }
    }
</style>