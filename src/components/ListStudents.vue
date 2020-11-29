<template>
    <div>
        <b-table 
            striped 
            hover 
            :fields="fields" 
            :items="items"
        >
        
          <template #cell(show_details)="row">

        
            <b-button size="sm" @click="handleDetails(row.item.id)" class="mr-2">
                
                Show Details 

            </b-button>


          </template>
        
        </b-table>
    </div>
</template>
<script>

import api from '../services/api'

export default {

    name: 'ListStudents',

    data() {
        return {
            items: [],
            fields:[

                {
                    key: 'name', 
                    label: 'Name:', 
                    sortable: true
                },
                {
                    key: 'email', 
                    label: 'E-mail:',
                    sortable: false
                },
                {
                    key: 'phone', 
                    label: 'TelePhone:',
                    sortable: true
                },

                
                {
                    key: 'show_details', 
                    label: 'Actions:',
                    sortable: false
                }

            ]

        }
        
    },
    mounted() {
        this.listStudents()
    },
    methods: {
        listStudents() {

            api.get('students').then(response => {

                const { data } = response
                this.items = data

            })
        },

        handleDetails( user ){

            window.location.href = `/student/edit/${ user }`;

        }

    },
    components: {

    }   
}
</script>
<style>

</style>