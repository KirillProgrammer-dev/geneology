<template>
    <div class="d-flex justify-center">
        <v-card max-width="50%" class="mt-12 pa-10">
            <v-card-title>
                Регистрация
            </v-card-title>
            <v-stepper v-model="e1">
                <v-stepper-header>
                <v-stepper-step
                    :complete="e1 > 1"
                    step="1"
                >
                    Основная информация
                </v-stepper-step>

                <v-divider></v-divider>

                <v-stepper-step
                    :complete="e1 > 2"
                    step="2"
                >
                    Контакты
                </v-stepper-step>

                <v-divider></v-divider>

                <v-stepper-step step="3">
                    Регистрационая информация
                </v-stepper-step>
                </v-stepper-header>

                <v-stepper-items>
                <v-stepper-content step="1">
                    <v-text-field
                        label="Введите ваше имя"
                        v-model="name"
                        outlined
                        type="text"
                    ></v-text-field>
                    <v-text-field
                        label="Введите вашу фамилию"
                        v-model="lastname"
                        outlined
                        type="text"
                    ></v-text-field>
                    <v-menu
                        ref="menu"
                        v-model="menu"
                        :close-on-content-click="false"
                        transition="scale-transition"
                        offset-y
                        max-width="290px"
                        min-width="auto"
                    >
                        <template v-slot:activator="{ on, attrs }">
                            <v-text-field
                                v-model="date"
                                label="Ваша дата рождения"
                                hint="MM/DD/YYYY format"
                                persistent-hint
                                prepend-inner-icon="mdi-calendar"
                                v-bind="attrs"
                                @blur="date = parseDate(date)"
                                v-on="on"
                                outlined
                            ></v-text-field>
                        </template>
                        <v-date-picker
                            v-model="date"
                            no-title
                            @input="menu = false"
                        ></v-date-picker>
                    </v-menu>

                    <v-btn
                    color="primary"
                    @click="e1 = 2"
                    >
                    Далее
                    </v-btn>
                </v-stepper-content>

                <v-stepper-content step="2">
                    <v-otp-input
                        v-model="phone"
                        length="11"
                        type="number"
                    ></v-otp-input>
                    <v-text-field
                        label="Введите почту"
                        v-model="email"
                        outlined
                        type="email"
                    ></v-text-field>
                    <v-text-field
                        label="Введите вашу страницу в соц сетях"
                        v-model="site"
                        outlined
                        type="text"
                    ></v-text-field>

                    <v-btn
                    color="primary"
                    @click="e1 = 3"
                    >
                        Далее
                    </v-btn>
                </v-stepper-content>

                <v-stepper-content step="3">
                    <v-text-field
                        label="Введите имя пользователя"
                        v-model="username"
                        outlined
                        type="text"
                    ></v-text-field>
                    <v-text-field
                        label="Введите пароль"
                        v-model="password"
                        outlined
                        type="password"
                    ></v-text-field>


                    <v-btn @click="registrate(name, lastname, date, phone, email, site, username, password)"
                    color="primary">
                        Регистрация
                    </v-btn>
                </v-stepper-content>
                </v-stepper-items>
            </v-stepper>
        </v-card>
        <v-overlay
            :z-index="1"
            :value="overlay"
            @click="overlay = !overlay"
        >
            <v-alert
                :value="alert"
                color="pink"
                dark
                border="top"
                icon="mdi-home"
                transition="scale-transition"
            >
                Пожалуйста заполните все обязательные поля в форме
            </v-alert>
        </v-overlay>
        </div>
</template>
<script>
export default {
    name: "Registration",
    data: () => ({
        name: null,
        lastname: null,
        password: null,
        site: null,
        email: null, 
        phone: null, 
        date: null,
        username: null, 
        menu: null,
        e1: 1,
        ok: true,
        step_error: 0,
        overlay: 0,
        alert: 1,
    }),
    methods: {
        registrate(name, lastname, date, phone, email, site, username, password){
            if (name != null && lastname != null && date != null && phone != null && email != null && username != null && password != null){
                this.axios.post("https://61f414d810f0f7001768c7e8.mockapi.io/api/social/users", {
                    name: name,
                    lastname: lastname,
                    date: date,
                    tel: phone,
                    email: email,
                    website: site,
                    username: username,
                    password: password,
                }).then(r => {
                    this.$router.push("/");
                    r
                });
            }
            else{
                if (name == null || lastname == 0 || date == null){
                    this.step_error = 1
                }
                else if (phone == null || email == null){
                    this.step_error = 2;
                }
                else if (username == null || password == null){
                    this.step_error = 3;
                }
                this.ok = false;
            }
        }
    },
    watch:{
        ok(){
            if (this.ok == false){
                this.overlay = !this.overlay;
                this.e1 = this.step_error;
                this.ok = !this.ok;
            }
        }
    }
}
</script>
<style>
.v-overlay__content {
    display: flex;
    justify-content: center;
}
</style>
