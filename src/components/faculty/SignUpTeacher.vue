<template>
    <section class="section">
        <div class="columns">
            <div class="column is-4 is-offset-4">
                <h2 class="title has-text-centered">Signup</h2>

                <form method="POST" @submit.prevent="signup">
                    <div class="field">
                        <label class="label">First Name</label>
                        

                        <p class="control">
                            <input
                                type="text"
                                class="input"
                                v-model="firstname">
                        <label class="label">Last Name</label>
                            <input
                                type="text"
                                class="input"
                                v-model="lastname">
                         
                        </p>
                    </div>

                    <div class="field">
                        <label class="label">E-Mail Address</label>

                        <p class="control">
                            <input
                                type="email"
                                class="input"
                                v-model="email">
                        </p>
                    </div>

                    <div class="field">
                        <label class="label">Password</label>

                        <p class="control">
                            <input
                                type="password"
                                class="input"
                                v-model="password">
                        </p>
                    </div>

                    <p class="control">
                        <button class="button is-primary is-fullwidth is-uppercase">SignUp</button>
                    </p>
                </form>
            </div>
        </div>
    </section>
</template>

<script>
import firebase from 'firebase'

export default {
    name: 'SignUp',
    data () {
        return {
            firstname: '',
            lastname: '',
           
            email: '',
            password: ''
        }
    },
    methods: {
        signup: function(){
            firebase.auth().createUserWithEmailAndPassword(this.email,this.password).then(
                (user)=>{
                    this.$router.replace('teacherhome')
                },
                function(err){
                    alert('OOps.' +err.message)
                }
            );
        }
        }
    }
</script>