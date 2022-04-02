<template>
    <div class="page-add-clients">

        <div class="breadcrumb" aria-label="breadcrumbs">
            <ul>
                <li><router-link to="/dashboard">Dashboard</router-link></li>
                <li><router-link to="/dashboard/clients" aria-current="True">Clients</router-link></li>
                <li class="is-active"><router-link to="/dashboard/clients/add" aria-current="True">Add</router-link></li>
            </ul>
        </div>

        <div class="columns is-multiline">
            <div class="column is-12">
                <h1 class="title">Add Client</h1>
            </div>

            <div class="column is-6">

                <div class="field">
                    <label>Name</label>
                    <div class="control">
                        <input type="text" class="input" v-model="client.name">
                    </div>
                </div>
           
           
                <div class="field">
                    <label>E-mail</label>
                    <div class="control">
                        <input type="email" class="input" v-model="client.email">
                    </div>
                </div>
           
           
                <div class="field">
                    <label>Address 1</label>
                    <div class="control">
                        <input type="text" class="input" v-model="client.address1">
                    </div>
                </div>

            
                <div class="field">
                    <label>Address 2</label>
                    <div class="control">
                        <input type="text" class="input" v-model="client.address2">
                    </div>
                </div>

            </div>

            <div class="column is-6">

                <div class="field">
                    <label>Zipcode</label>
                    <div class="control">
                        <input type="text" class="input" v-model="client.zipcode">
                    </div>
                </div>

                <div class="field">
                    <label>Place</label>
                    <div class="control">
                        <input type="text" class="input" v-model="client.place">
                    </div>
                </div>

                <div class="field">
                    <label>State</label>
                    <div class="control">
                        <input type="text" class="input" v-model="client.state">
                    </div>
                </div>

                <div class="field">
                    <label>Country</label>
                    <div class="control">
                        <input type="text" class="input" v-model="client.country">
                    </div>
                </div>
            
            </div>

            <div class="column is-12">
                <div class="field">
                    <div class="control">
                        <button class="button is-success" @click="submitForm">Submit</button>
                    </div>                
                </div>
            </div>

        </div>
    </div>
</template>

<script>
import axios from 'axios'
import { toast } from 'bulma-toast' 

export default{
    name: 'addClient',
    data() {
        return {
            client: {}
        }
    },
    methods: {
        submitForm() {
            axios
                .post("/api/v1/clients/", this.client)
                .then(Response => {
                    toast({
                            message: 'The Client was Saved',
                            type: 'is-success',
                            dismissible: 'true',
                            pauseOnHover: 'true',
                            duration: '2000',
                            position: 'center'
                        })
                    this.$router.push('/dashboard/clients')
                })
                .catch(error => {
                    console.log(JSON.stringify(error))
                })
        }

    }

}
</script>