<template>
  <div>

    <b-container>
      <b-row class="vh-100 text-center" align-v="center">
        <b-col>
          
          {{message}}

        </b-col>
      </b-row>
    </b-container>

  </div>
</template>
<script>

  import api from "@/services/api";

export default {


  name: "Home",
  
  data(){

    return {

      message: "Loading..."

    };

  },

  created(){

    this.showHomeMessage();

  },

  methods:{

    showHomeMessage(){

      api.get('')
      .then(( response )=>{

          const {data} = response;
          this.message = data;

      });

    }

  }
};
</script>
<style></style>