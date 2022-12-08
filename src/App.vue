<template>
  <div>
    <div>
      {{JSON.stringify(formValues,null,2)}}
    </div>
  <h1>Vue Forms</h1>
  <form @submit="submit"> 
    <div>
      <label for="name">Name : </label>
      <input type="text" id="name" v-model="formValues.name"/>
      <br />
      
      <br />
      <label for="about">About : </label>
      <textarea id="about" v-model="formValues.about" />
    </div>

    <br />
    <div>
      <label for="country" >Country : </label>
      <select id="country" v-model="formValues.country">
        <option value="">Selct Your Country</option>
        <option value="India">India</option>
        <option value="USA">USA</option>
        <option value="Russia">Russia</option>
        <option value="Australia">Australia</option>
        <option value="Brazil">Brazil</option>
        <option value="Mexico">Mexico</option>
        <option value="Europe">Europe</option>
      </select>
    </div>
    <br />
    <div>
      <label for="socialhandle">Select Your Social Handles</label>
      <br />
      <select id="socialhandle" multiple v-model="formValues.socialHandles">
        <option value="Facebook">FB</option>
        <option value="Instagram">Instagram</option>
        <option value="snapchat">snapchat</option>
        <option value="Twitter">Twitter</option>
        <option value="Whatsapp">Whatsapp</option>
      </select>
    </div>
    <br />
    <div>
      <label for="gender">Enter Gender : </label>
      <br />
      <input type="radio" id="male" v-model="formValues.gender" value="Male" />
      <label for="male">Male</label>
      <input type="radio" id="female" v-model="formValues.gender" value="Female" />
      <label for="female" >Female</label>
      <input type="radio" id="others" v-model="formValues.gender" value="Rather Not Say"/>
      <label for="others">Rather Not Say</label>
    </div>
    <br />
    <div>
      <input type="checkbox" id="aboveage" v-model="formValues.aboveage" 
      true-value="eligible" false-value="not-eligible" />
      <label for="aboveage" >Are you eligible to Vote (Above 18)?</label>
    </div>
    <button>Submit</button>

  </form>
  </div>

</template>

<script>
import { ref } from 'vue';
export default {
  name: 'App',
  setup(){
    const formValues = ref(
      {
        name:'',
        about:'',
        country :'',
        socialHandles: [],
        gender:'',
        aboveage:'not-eligible'
      }
    )
    function submitForm(event){
      event.preventDefault();
      if(!formValues.value.name || formValues.value.name.length <10){
        console.log("Enter Valid Phone Number!")
      }
      if(!formValues.value.country){
        console.log("Enter Valid Country!")
      }
      if(!formValues.value.gender){
        console.log("Enter Valid Gender!")
      }


    
    }

    return {
      formValues,
      submit:submitForm
    }

  },

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
