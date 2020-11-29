<template>
  <div>
    
    <b-container>

      <b-row class="justify-content-md-center mt-4">

        <b-col col md="8">

          <b-card 
            header="Update student data"
            header-bg-variant="dark"
            header-text-variant="white"
          >
          
          <b-card-text>
             <b-form @submit.prevent="handleUpdate">

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

                  😎 Update

                </b-button>

              </b-form-group>

            </b-form>

             <b-button size="sm" @click="handleGoBack()" class="btn btn-warning">
                
                Go Back

            </b-button>

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
  
  created(){

    this.getInfo();

  },

  methods: {

        getInfo(){

            api.get(`students/${this.$route.params.id}`)
            .then(( response )=>{

                const { data } = response;
                
                this.student = data;
                
                

            })
            .catch(()=>{

                alert('Unfortunately the user was not registered');
            

            });
        },

        handleUpdate(){

            api.put(`students/${this.$route.params.id}`)
            .then(()=>{

                alert('The user was updated com sucesso')

            })
            .catch(()=>{

                alert('Could not update user');


            });


        },

        handleGoBack(){

            this.$router.go(-1)

        }

  }
};
</script>