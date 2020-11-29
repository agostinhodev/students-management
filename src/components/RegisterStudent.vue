<template>
  <div>
    
    <b-container>

      <b-row class="justify-content-md-center mt-4">

        <b-col col md="8">

          <b-card 
            header="Please enter student data"
            header-bg-variant="dark"
            header-text-variant="white"
          >
          
          <b-card-text>
             <b-form @submit.prevent="handleRegister">

              <b-form-group 
                description="What's him name?"
                label="Name: 🤔">

                <b-form-input
                v-model="student.name"
                required
                >
                </b-form-input>

              </b-form-group>

              <b-form-group 
                description="E-mail:"
                label="Please provide a e-mail to contact">

                <b-form-input
                v-model="student.email"
                required
                type="email"
                min=1
                >
                </b-form-input>

              </b-form-group>

              <b-form-group 
                description="Phone:"
                label="Please provide a phone to contact">

                <b-form-input
                v-model="student.phone"
                required
                type="number"
                min=1
                >
                </b-form-input>

              </b-form-group>

              <b-form-group>

                <b-button
                
                type="submit"
                variant="outline-dark"

                >

                  😎 Submit

                </b-button>

              </b-form-group>

            </b-form>
          </b-card-text>
          
          </b-card>

        </b-col>

      </b-row>

    </b-container>
   
  </div>
  
</template>

<script>

import api from "@/services/api";
export default {

  
  name: "RegisterStudent",
  data() {
    return {

      student: {
        name: "",
        email: "",
        phone: ""
      }

    };
  },
  components: {
    
  },
  methods: {
      onReset() {
        this.student = {
          name: "",
          email: "",
          phone: ""
        }
      }, 

      handleRegister(){

        const {
          name,
          email,
          phone,
        } = this.student;


        api.post('students', { 
          name,
          email,
          phone
        })
        .then(()=>{

          alert('The student was successfully registered');
          this.onReset();
         

        })
        .catch(()=>{

          alert('Unfortunately the user was not registered');
          

        });


      }
  }
};
</script>
<style>
</style>