<template>
  <form>
    <!-- v-model syncs the data in the input with the data properties -->
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
        <option value="Designer">Designer</option>
        <option value="Developer">Developer</option>
      </select>
    </div>
  </form>

  <p>Email: {{email}}</p>
  <p>Password: {{password}}</p>
</template>

<script>
export default {
  data() {
    return {
      email: 'abc@123.com',
      password: 'helloworld',
      role: ''
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
  }

  input {
    display: block;
    width: 100%;
    font-size: 18px;
    padding: 3px;
    border: none;
    border-bottom: 2px dashed rgb(139, 139, 139);
  }

  input:focus {
    outline: none;
    border-bottom: 2px solid rgb(139, 139, 139);
  }

  .field {
    margin-bottom: 40px;
  }
</style>