<template>
  <div>
    <h1>Survey Forms</h1>
    <div>
      <pre>
        {{JSON.stringify(formValues,null,2)}}
      </pre>
    </div>
    <form @submit="submitForm">
      <label for="name">Name</label>
      <input id="name" type="text" v-model="formValues.name" />
      <br />
      <label for="about">About</label>
      <textarea id="about" v-model="formValues.about" />
      <br />
      <div>
        <label for="country">Country</label>
        <select id="country" v-model="formValues.country">
          <option value="">Select a Country</option>
          <option value="India">India</option>
          <option value="USA">USA</option>
          <option value="Malaysia">Malaysia</option>
        </select>
      </div>
      <br />
      <div>
        <label for="social-handle">Social Handle</label>
        <select id="social-handle" multiple v-model="formValues.socialHandles">
          <option value="">Select the platforms you use</option>
          <option value="Twitter">Twitter</option>
          <option value="Facebook">Facebook</option>
          <option value="Instagram">Malaysia</option>
          <option value="Snapchat">Snapchat</option>
        </select>
      </div>
      <br />
      <div>
        <label for="gender">Enter Gender</label>
        <br />
        <input type="radio" id="male" v-model="formValues.gender" value="Male" />
        <label for="male">Male</label>
        <input type="radio" id="female" v-model="formValues.gender" value="Female" />
        <label for="feale">Female</label>
        <input type="radio" id="others" v-model="formValues.gender" value="Others" />
        <label for="others">Others</label>
      </div>
      <br />
      <div>
        <input id="aboveage" type="checkbox" true-value="yes" false-value="no" v-model="formValues.aboveage"/>
        <label for="aboveage">Are you above 18 ? </label>
      </div>
      <button>Submit</button>
    </form>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  name: "App",
  setup() {
    const formValues = ref({
      name: "",
      about: "",
      country: "",
      socialHandles: [],
      gender:'',
      aboveage: "no",
    });

    function submitForm(e) {
      e.preventDefault();
      console.log("FORMVALUES", formValues.value);
    }

    return {
      formValues,
      submitForm,
    };
  },
};
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
.form {
  display: table-column;
  justify-content: space-between;
  align-items: center;
}
</style>
