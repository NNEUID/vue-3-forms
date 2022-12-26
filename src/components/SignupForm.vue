<template>
  <form>
    <label>Email</label>
    <input type="email" required v-model="email">

    <label>Password</label>
    <input type="password" required v-model="password">

    <label>Role</label>
    <select v-model="role">
        <option value="Developer">Web Developer</option>
        <option value="Designer">Web Designer</option>
    </select>

    <div class="terms">
        <input type="checkbox" required v-model="terms">
        <label>Accept Terms and Conditions</label>
    </div>

    <!-- <div class="terms">
        <input type="checkbox" value="Serwaa" v-model="names">
        <label>Serwaa</label>
    </div>
    <div class="terms">
        <input type="checkbox" value="Noel" v-model="names">
        <label>Noel</label>
    </div>
    <div class="terms">
        <input type="checkbox" value="Prince" v-model="names">
        <label>Prince</label>
    </div> -->
  </form>


  <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Role: {{ role }}</p>
  <p>Terms Accepted: {{ terms }}</p>
  <!-- <p>Names: {{ names }}</p> -->
</template>

<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            role: '',
            terms: false,
            names: []
        }
    }
}
</script>

<style>
form {
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
}

label {
    display: inline-block;
    color: #aaa;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}

input, select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}

input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
}
</style>