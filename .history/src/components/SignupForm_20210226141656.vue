<template>
  <form>
    <div class="field">
      <label>Email: </label>
      <input type="email" required v-model="email" />
    </div>
    <div class="field">
      <label>Password: </label>
      <input type="password" required v-model="email" />
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      email: ''
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
</style>