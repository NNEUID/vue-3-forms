<template>
  <form @submit.prevent="handleSubmit">
    <label>Email</label>
    <input type="email" required v-model="email">

    <label>Password</label>
    <input type="password" required v-model="password">
    <div v-if="passwordError" class="error">{{ passwordError }}</div>

    <label>Role</label>
    <select v-model="role">
      <option value="Developer">Web Developer</option>
      <option value="Designer">Web Designer</option>
    </select>

    <label>Skills</label>
    <input type="text" v-model="tempSkill" @keyup="addSkill">
    <div class="pill" v-for="skill in skills" :key="skill">
      <span @click="deleteSkill(skill)">{{ skill }}</span>
    </div>

    <div class="terms">
      <input type="checkbox" required v-model="terms">
      <label>Accept Terms and Conditions</label>
    </div>

    <div class="submit">
      <button type="submit">Create an Account</button>
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


  <!-- <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Role: {{ role }}</p>
  <p>Skills: {{ skills }}</p>
  <p>Terms Accepted: {{ terms }}</p>
  <p>Names: {{ names }}</p> -->
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      role: '',
      terms: false,
      names: [],
      skills: [],
      tempSkill: '',
      passwordError: ''
    }
  },
  methods: {
    addSkill(e) {
      if(e.key === 'Shift' && this.tempSkill) {
        if(!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill)
        }
        this.tempSkill = ''
      }
    },
    deleteSkill(skill) {
      this.skills = this.skills.filter(item => {
         return skill !== item
      })
    },
    handleSubmit() {
      // validate password
      this.passwordError = this.password.length > 5 ?
      '' : 'Password must be at least 6 characters long'

      if(!this.passwordError) {
        console.log(this.email);
        console.log(this.password);
        console.log(this.role);
        console.log(this.skills);
        console.log(this.terms);
      }
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

input,
select {
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

.pill {
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  border-radius: 20px;
  background: #eee;
  letter-spacing: 1px;
  font-weight: bold;
  color: #777;
  cursor: pointer;
}

button {
  background: #0b6dff;
  border: 0;
  padding: 10px 20px;
  margin-top: 20px;
  color: white;
  border-radius: 20px;
}

.submit {
  text-align: center;
}

.error {
  color: #ff0062;
  margin-top: 10px;
  font-size: 0.8em;
  font-weight: bold;
}
</style>