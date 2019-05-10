<template>
  <div class="home">
       <h1>Adopt A New Best Friend</h1>
       <button class="btn btn-primary" @click="togglePetForm">Add New Pet</button>
       
        <div>
          <b-form @submit.prevent="submitForm"  v-if="petForm">
            

            <b-form-group id="input-group-2" label="Pet's Name:" label-for="input-2">
              <b-form-input
                id="input-2"
                v-model="form.first_name"
                required
                placeholder="Enter name"
              ></b-form-input>
            </b-form-group>

            <b-form-group id="input-group-3" label="Spcies:" label-for="input-3">
              <b-form-select
                id="input-3"
                v-model="form.species"
                :options="['cats','dogs']"
                required
              ></b-form-select>
            </b-form-group> 
              <b-form-group id="input-group-2" label="Pet's Age:" label-for="input-2">
              <b-form-input
                id="input-2" 
                type="number" 
                v-model="form.age"
                required
                placeholder="Enter Age"
              ></b-form-input>
              </b-form-group>
              <b-form-group id="input-group-2" label="Pet's Breed:" label-for="input-2">
              <b-form-input
                id="input-2" 
                type="text" 
                v-model="form.breed"
                required
                placeholder="Enter Breed"
              ></b-form-input>
            </b-form-group>
            

            <b-button type="submit" variant="primary">Submit</b-button>
          </b-form>
          <b-card class="mt-3" header="Form Data Result">
            <pre class="m-0">{{ form }}</pre>
          </b-card>
        </div>
  </div>
</template>

<script>
import {mapActions} from 'vuex'
export default {
  name: 'home',
  data() {
    return {
    petForm:false,
    form:{
      first_name:"" ,
      age: "" ,
      species: null
    }

    }
  },
  methods: {
    ...mapActions([
      'addPet'
    ]),
    togglePetForm() {
      this.petForm= !this.petForm
    },
    submitForm(){
      const { species, age, first_name,breed }=this.form 
      const payload={
        species,
        pet:{
          first_name ,
          age ,
          breed,
        }
      }
      this.addPet(payload)
      this.form={
        
      }
    }
  }
}
</script>
