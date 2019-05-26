<template>
  <div class="column">
    <div class="card">
     <div class="card-content">
     
        <p class="title is-3 has-text-grey">
          {{ title }}
        </p>
        <p class="subtitle is-6 has-text-grey">
          Crea una cuenta gratis hoy mismo.
        </p>
        <form @submit.prevent="validateBeforeSubmit">
        <b-field label="Nombre de usuario"
                :type="{'is-danger': errors.has('username')}"
                :message="[{
                    'Llene el campo de nombre de usuario' : errors.firstByRule('username', 'required'),
                   
                }]">
                <b-input type="text" v-model="username" name="username" v-validate="{ required: true}" />
        </b-field>
         <b-field label="Correo"
            :type="{'is-danger': errors.has('email')}"
            :message="[{
                 'Llene el campo de correo' : errors.firstByRule('email', 'required'),'Llene el campo de contraseña' : errors.firstByRule('password','required'),
             }]">
                <b-input type="text" v-model="email" name="email" v-validate="{ required: true}" />
        </b-field>
        <b-field label="Contraseña"
             :type="{'is-danger': errors.has('password')}"
                :message="[{
                    'Llene el campo de contraseña' : errors.firstByRule('password','required') 
                   
                },
                'la contraseña debe tener mas de 8 carcateres']">
                <b-input type="password" v-model="password" name="password" maxlength="30" v-validate="'required|min:8'" />
        </b-field>
        <b-field label="Confirm password"
                :type="{'is-danger': errors.has('confirm-password')}"
                :message="[{
                    'Se requiere la confirmacion de la contraseña' : errors.firstByRule('confirm-password', 'required'),
                    'Contraseña incorrecta' : errors.firstByRule('confirm-password', 'is')
                }]">
                <b-input type="password" v-model="confirmPassword" name="confirm-password"
                    maxlength="30" v-validate="{ required: true, is: password }" />
            </b-field>
         <button type="submit" class="button is-primary"> Submit </button>
       </form>
        </div>
      </div>
      
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import VeeValidate from 'vee-validate'

    Vue.use(VeeValidate, {
        events: ''
    })

export default {
   data() {
            return {
                username: null,
                email: null,
                password: null,
                confirmPassword: null
            }
        },  methods: {
            validateBeforeSubmit() {
                this.$validator.validateAll().then((result) => {
                    if (result) {
                        this.$toast.open({

                        })
                        return;
                    }
                    this.$toast.open({
                        message: 'Revise los campos llenados',
                        type: 'is-danger',
                        position: 'is-bottom'
                    })
                });
            }
        },
  props: {
    title: {
      type: String,
      required: true
    }
  }
}
</script>

