<template>
    <div>
        <login-form :authenticate="authenticate()" />
    </div>
</template>
<script>
import LoginForm from "../components/LoginForm.vue"


export default {
    methods: {
        authenticate(name, password){
            this.axios.get("https://61f414d810f0f7001768c7e8.mockapi.io/api/social/users").then(response => {
                for(let i of response.data){
                    if (i.username == name){
                        if (i.password == password){
                            this.$emit("login", i)
                            this.$router.push("/");
                        }
                        else{
                            window.alert("Ваш пароль неверен")
                        }
                    }
                }
        });
        }
    }, 
    components: {
        LoginForm
    }
}
</script>
