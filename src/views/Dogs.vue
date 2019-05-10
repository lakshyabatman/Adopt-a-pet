<template>
    <div>
        <h3>Dogs For Adoption
        </h3>
        <b-table :items="dogs">
      <template slot="first_name" slot-scope="data">
        <router-link :to="`/pet/dogs/${data.index}`">{{data.value}}</router-link>
      </template>
    </b-table>
    </div>
</template>

<script>
import {mapState} from 'vuex'

export default {
    data(){
     return {

     }   
    },
    computed:{
        ...mapState([
            "dogs"
        ])
    }
}
</script>
