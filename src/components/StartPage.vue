<template>
    <div>
        <div class="background-image">
            <div class="container">
                <div class="content">
                    <div class="image-wrapper">
                        <b-img :src="vault" fluid alt="Responsive image" rounded="circle"></b-img>
                    </div>
                    <div class="vault-info">
                        <b-card
                            class="vault-card mb-2 mt-4"
                        >
                                <b-card-text>
                                    Voer de juiste code in om het geheim te ontrafelen!
                                    <b-input-group class="mt-3">
                                        <template #append>
                                        <b-input-group-text><strong class="text-danger">!</strong></b-input-group-text>
                                        </template>
                                        <b-form-input v-model="text" placeholder="Code" :state="state"></b-form-input>
                                    </b-input-group>
                                    <p class="mb-1 mt-2" v-if="evenTries" >foute Code, probeer het nog een keer!</p>
                                    <p class="mb-1 mt-2" v-if="unevenTries" >Nog steeds fout</p>
                                    <b-button class="mt-2" variant="danger" @click="showModal">Invoeren</b-button>
                                </b-card-text>
                        </b-card>
                    </div>
                    <b-modal title="GEWONNEN YEAH" v-model="modalShow" centered id="bv-modal-example" hide-footer>
                        <h3>Goed gedaan team Family!</h3>
                          <b-embed
                                type="iframe"
                                aspect="16by9"
                                src="https://www.youtube.com/embed/FBvoU-UiW84"
                                allowfullscreen
                        ></b-embed>
                    </b-modal>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import vault from "../assets/closed_vault.jpg"

export default {
        data: function () {
            return {
                vault : vault,
                text: '',
                modalShow: false,
                try: 0,
                state: null,
                unevenTries: false,
                evenTries: false,
            }
        },
        methods: {
            showModal() {
                const key = "lagloire101";
                if (this.text.toLowerCase() === key){
                    this.modalShow = true;
                    this.evenTries = false ;
                    this.unevenTries = false ;
                } else if (this.try % 2 !== 0){
                    this.try += 1;
                    this.evenTries = false ;
                    this.unevenTries = true ;
                }  else {
                    this.try += 1;
                    this.unevenTries = false ;
                    this.evenTries = true;
                }
            }
        },
    }
</script>

<style>
    .vault-info {
        display: flex;
        justify-content: center;
    }
    
    .card {
        color: red;
        background-color: black !important;
    }

    .card-body {
        background-color: black;
        max-width: 200px;
    }

    .orange {
        color: orange;
    }

    .darkred {

    }

    .background-image {
        background-color: #8E8D8D;
    }

    .vault-image {
        height:100%;
        width: 100%;
    }
</style>