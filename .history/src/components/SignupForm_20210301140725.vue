<template>
  <form>
    <!-- 
      v-model syncs the data in the input with the data properties.
      We can set the default value of a form element by entering it
      in the data().
    -->
    <div class="field">
      <label>Email: </label>
      <input type="email" required v-model="email" />
    </div>
    <div class="field">
      <label>Password: </label>
      <input type="password" required v-model="password" />
    </div>
    <div class="field">
      <label>Role: </label>
      <select v-model="role">
        <option value="">Please choose...</option>
        <option value="Designer">Web Designer</option>
        <option value="Developer">Web Developer</option>
      </select>
    </div>

    <div class="field">
      <label>Skills: </label>
      
      <input type="text" required v-model="tempSkill" @keyup="addSkill" />
      <div v-for="skill in skills" class="skill-item" :key="skill" @click="removeSkill(skill)">
        {{skill}}
      </div>
    </div>

    <div class="field checkboxField">
      <input type="checkbox" required v-model="terms" />
      <label>Agree T&amp;Cs</label>
    </div>

    <div class="field checkboxField">
      <input type="checkbox" value="Cat" v-model="animal" /><label>Cat</label>
      <input type="checkbox" value="Dog" v-model="animal" /><label>Dog</label>
      <input type="checkbox" value="Dinosaur" v-model="animal" /><label>Dinosaur</label>
    </div>

    <div class="submit-button-wrapper">
      <button>Submit</button>
    </div>
  </form>

  <p>Email: {{email}}</p>
  <p>Password: {{password}}</p>
  <p>Role: {{role}} </p>
  <p>terms: {{terms}} </p>
  <p>Animals: {{animal}} </p>
</template>

<script>
export default {
  data() {
    return {
      email: 'abc@123.com', // I set the default value here
      password: '',
      role: '', 
      tempSkill: '',
      terms: false, // checkbox is a boolean
      skills: [],
      animal: [] // Multiple checkboxes for this creates an array
    }
  },
  methods: {
    addSkill(e) {
      if (e.key === 'Enter' && this.tempSkill) {

        // If the skill already exists, don't add to array
        if(!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
        }

        this.tempSkill = '';
      }
    },
    removeSkill(skill, e) {            
      this.skills = this.skills.filter((skillItem) => {
        return skill !== skillItem; // if this returns false, this item will be taken out of the array returned
      });
    }
  }
}
</script>

<style scoped>
  form {
    max-width: 420px;
    border-radius: 5px;
    background: white;
    padding: 20px;
    margin: 0 auto;
  }

  label {
    font-weight: 700;
    display: block;
    text-align: left;
    margin-bottom: 5px;
  }

  input, select {
    display: block;
    width: 100%;
    font-size: 18px;
    padding: 3px;
    border: none;
    border-bottom: 2px dashed rgb(139, 139, 139);
  }

  input:focus,
  select:focus {
    outline: none;
    border-bottom: 2px solid rgb(139, 139, 139);
  }

  input[type=checkbox] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 1px;
  }

  .checkboxField label {
    display: inline-block;
    width: auto;
    text-align: left;
  }

  .field {
    text-align: left;
    margin-bottom: 40px;
  }

  .skill-item {
    display: inline-block;
    margin-top: 5px;
    margin-left: 5px;
    border-radius: 20px;
    height: 20px;
    padding: 5px 10px;
    background-color: darkgray;
    color: white;
  }
  .skill-item:hover {
    font-weight: bold;
    cursor: pointer;
  }

  .submit-button-wrapper button {
    box-shadow: 0px 0px 0px 2px #9fb4f2;
    background:linear-gradient(to bottom, #7892c2 5%, #476e9e 100%);
    background-color:#7892c2;
    border-radius:10px;
    border:1px solid #4e6096;
    display:inline-block;
    cursor:pointer;
    color:#ffffff;
    font-family:Arial;
    font-size:19px;
    padding:12px 37px;
    text-decoration:none;
    text-shadow:0px 1px 0px #283966;
  }

  .submit-button-wrapper button:hover {
    background:linear-gradient(to bottom, #476e9e 5%, #7892c2 100%);
    background-color:#476e9e;
  }

  .submit-button-wrapper button:active {
    position:relative;
    top:1px;
  }
</style>