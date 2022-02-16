<template>
    <v-container
    tag="div"
    class="mx-0"
    fluid>
        <div class="text-h1 px-40">
            Начни поиск прямо сейчас
        </div>
        <v-stepper alt-labels v-model="e1">
            <v-stepper-header>
                <div v-for="step in steps_amount" :key="step" >
                    <v-stepper-step :step="step" editable :complete="e1 > step">
                        {{ steps[step] }}
                    </v-stepper-step>
                    <v-divider v-if="step !== steps_amount"/>
                </div>
            </v-stepper-header>
            <v-stepper-items>
                <v-stepper-content
                    step="1"
                >
                    <v-form v-model="valid">
                        <v-container>
                        <v-row>
                            <v-col
                            cols="12"
                            md="4"
                            >
                                <v-text-field
                                    v-model="lastname"
                                    :rules="nameRules"
                                    label="Фамилия"
                                    required
                                ></v-text-field>
                            </v-col>

                            <v-col
                            cols="12"
                            md="4"
                            >
                                <v-text-field
                                    v-model="firstname"
                                    :rules="nameRules"
                                    label="Имя"
                                    required
                                ></v-text-field>
                            </v-col>

                            <v-col
                            cols="12"
                            md="4"
                            >
                                <v-text-field
                                    v-model="middlename"
                                    :rules="nameRules"
                                    label="Отчество"
                                    required
                                ></v-text-field>
                            </v-col>
                        </v-row>
                        </v-container>
                    </v-form>

                    <v-btn
                        color="primary"
                        @click="nextStep(1)"
                    >
                        Дальше
                    </v-btn>

                    <v-btn text>
                        Cancel
                    </v-btn>
                </v-stepper-content>
                <v-stepper-content
                    step="2"
                >
                    <v-text-field
                        v-model="place"
                        :rules="nameRules"
                        label="Место"
                        required
                    ></v-text-field>

                    <v-btn
                        color="primary"
                        @click="nextStep(2)"
                    >
                        Continue
                    </v-btn>

                    <v-btn text>
                        Cancel
                    </v-btn>
                </v-stepper-content>
                <v-stepper-content
                    step="3"
                >
                    <v-container>
                        <v-row>
                            <v-select
                            v-model="from"
                            :items="years"
                            label="От"
                            ></v-select>
                            <v-divider vertical
                            class="mx-10"/>
                            <v-select
                            v-model="before"
                            :items="years"
                            label="До"
                            ></v-select>
                        </v-row>
                    </v-container>

                    <v-btn
                        color="primary"
                        @click="nextStep(3)"
                    >
                        Continue
                    </v-btn>

                    <v-btn text>
                        Cancel
                    </v-btn>
                </v-stepper-content>
            </v-stepper-items>
        </v-stepper>
    </v-container>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    data: () => ({
        steps: {
            1: "ФИО",
            2: "Место жительства",
            3: "Дополнительная информация",
        },
        steps_amount: 3,
        e1: 1,
        valid: false,
        firstname: '',
        lastname: '',
        middlename: '',
        nameRules: [
            /*v => !!v || 'Name is required',
            v => v.length <= 10 || 'Name must be less than 10 characters',*/
        ],
        place: "",
        years: [],
        from: 1800,
        before: 1900,
    }),
    methods: {
        nextStep (n) {
            if (n === this.steps_amount) {
                this.e1 = 1
            } else {
                this.e1 = n + 1
            }
        }
    },
    watch: {
      steps (val) {
        if (this.e1 > val) {
          this.e1 = val
        }
      },
    },
    mounted(){
        for(let i = 1700; i < 1999; i++){
            this.years.push(i)
        }
    },
})
</script>

