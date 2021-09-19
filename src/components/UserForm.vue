<template>
  <form @submit="handleSubmit">
        Förnamnt: <input type="text" v-model="user.firstName" id="firstName"><br />
        Efternamn: <input type="text" v-model="user.lastName" id="lastName"><br />
        <button>Spara</button>
    </form>
</template>

<script>
export default {
    name: "UserForm",
    props: {
        user: {
            type: Object,
        }
    },
    methods: {
        handleSubmit(event) {
            //event.preventDefault();
            console.log("I UserForm submit!", event);

                this.$emit("save", event);

        }
    }
}
</script>

<style>

</style>