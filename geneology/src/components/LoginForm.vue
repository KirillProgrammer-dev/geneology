<template>
    <div class="d-flex justify-center">
        <v-card width="600px" class="mt-12 pa-10">
            <v-card-title>
                Войдите в аккаунт
            </v-card-title>

            <v-text-field
                label="Введите ваше имя"
                v-model="name"
                outlined
            ></v-text-field>

            <v-text-field
                label="Введите пароль"
                v-model="password"
                outlined
                type="password"
            ></v-text-field>

            <v-btn @click="$emit(authenticate, name, password)">
                Войти
            </v-btn>
        </v-card>
    </div>
</template>
<script>
export default {
    name: "LoginForm",
    data: () => ({
        name: null,
        password: null,
    }),
}
</script>
