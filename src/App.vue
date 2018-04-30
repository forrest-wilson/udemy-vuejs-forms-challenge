<template>
    <div class="container">
        <form v-if="!isSubmitted">
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <!-- Exercise 1 -->
                    <!-- Create a Signup Form where you retrieve the following Information -->
                    <!-- Full Name (First Name + Last Name) -->
                    <!-- Mail -->
                    <!-- Password -->
                    <!-- Store Data? Yes/No -->

                    <!-- Exercise 2 -->
                    <!-- Only display the Form if it has NOT been submitted -->
                    <!-- Display the Data Summary ONCE the Form HAS been submitted -->

                    <!-- Exercise 3 -->
                    <!-- Edit the Example from above and create a custom "Full Name" Control -->
                    <!-- which still holds the First Name and Last Name Input Field -->

                    <div class="form-group">
                        <label for="firstname">First Name</label>
                        <input
                                type="text"
                                id="firstname"
                                class="form-control"
                                v-model="userData.name.first">
                    </div>

                    <div class="form-group">
                        <label for="lastname">Last Name</label>
                        <input
                                type="text"
                                id="lastname"
                                class="form-control"
                                v-model="userData.name.last">
                    </div>

                    <div class="form-group">
                        <label for="email">Mail</label>
                        <input
                                type="email"
                                id="email"
                                class="form-control"
                                v-model="userData.email">
                    </div>

                    <div class="form-group">
                        <label for="password">Password</label>
                        <input
                                type="password"
                                id="password"
                                class="form-control"
                                v-model="userData.password">
                    </div>
                </div>
            </div>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
                    <label for="male">
                        <input
                                type="radio"
                                id="male"
                                value="Yes"
                                v-model="userData.storeData"> Yes &nbsp;
                    </label>
                    <label for="female">
                        <input
                                type="radio"
                                id="female"
                                value="No"
                                v-model="userData.storeData"> No
                    </label>
                </div>
            </div>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
                    <input type="submit" @click.prevent="submitted">
                </div>
            </div>
        </form>
        <hr>
        <div class="row" v-if="isSubmitted">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <div class="panel panel-default">
                    <div class="panel-heading">
                        <h4>Your Data</h4>
                    </div>
                    <div class="panel-body">
                        <p>Full Name: <app-full-name
                            :firstName="userData.name.first" :lastName="userData.name.last"></app-full-name>
                        </p>
                        <p>Mail: {{ userData.email }}</p>
                        <p>Password: {{ userData.password }}</p>
                        <p>Store in Database?: {{ userData.storeData }}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import FullName from "./FullName.vue";

    export default {
        data() {
            return {
                userData: {
                    name: {
                        first: "",
                        last: ""
                    },
                    email: "",
                    password: "",
                    storeData: "Yes"
                },
                isSubmitted: false
            };
        },
        methods: {
            submitted() {
                this.isSubmitted = true;
            }
        },
        components: {
            'app-full-name': FullName
        }
    }
</script>