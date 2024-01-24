<template>
    <form @submit.prevent="submitForm()">
        <div class="mb-3">
            <label for="email" class="form-label">Email</label>
            <input required v-model="newMail.email" type="email" class="form-control" id="email"
                aria-describedby="emailHelp">
            <div id="emailHelp" class="form-text text-white">Insert your email. <br>We'll never share your email with
                anyone else.</div>
        </div>
        <div class="mb-3">
            <label for="name" class="form-label">Name</label>
            <input required v-model="newMail.name" type="text" class="form-control" id="name">
            <div id="nameHelp" class="form-text text-white">Insert your name</div>
        </div>
        <div class="mb-3">
            <label for="address" class="form-label">Address</label>
            <input required v-model="newMail.address" type="text" class="form-control" id="address">
            <div id="addressHelp" class="form-text text-white">Insert your address</div>
        </div>
        <div class="mb-3">
            <label for="message" class="form-label">Message</label>
            <textarea required v-model="newMail.message" rows="5" class="form-control" id="message"></textarea>
            <div id="messageHelp" class="form-text text-white">Insert your message</div>
        </div>
        <button type="submit" class="btn btn-primary me-3">Submit</button>
        <button type="reset" class="btn btn-danger">Reset</button>
    </form>
</template>

<script>

import { store } from '../store.js';
import axios from 'axios';
export default {
    name: 'ContactForm',
    data() {
        return {
            store,
            newMail: {
                name: "",
                email: "",
                address: "",
                message: ""
            }

        }
    },
    methods: {
        submitForm() {
            axios.post(this.store.apiUrl + "contacts", this.newMail).then((res) => {
                console.log(res.data);
                this.newMail = {
                    name: "",
                    email: "",
                    address: "",
                    message: ""
                }
            }).catch((err) => {
                console.log('error', err);
            })
        }
    }
}
</script>

<style lang="scss" scoped></style>