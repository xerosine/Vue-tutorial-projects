<template>
    <div>
        <form @submit.prevent="handleSubmit">
            <label>Email</label>
            <input type="text" v-model="email">

            <label>Password</label>
            <input type="text" v-model="password">
            <div class="error">{{ passwordError }}</div>

            <label>Role</label>
            <select v-model="role">
              <option value="developer">Web Developer</option>
              <option value="designer">Web Designer</option>
            </select>

            <label>Skills</label>
            <input type="text" v-model="tempSkill" @keyup.alt="addSkill">
            <div class="pill" v-for="skill in skills" :key="skill" @click="deleteSkill(skill)">
              {{ skill }}
            </div><br>

            <input type="checkbox" v-model="terms">
            <label>Accept terms and conditions</label>

          <div>
            <label>Familiarities</label><br>
            <label>ML</label>
            <input type="checkbox" value="Machine Learning" v-model="names">
            <label>DS</label>
            <input type="checkbox" value="Data Science" v-model="names">
            <label>AI</label>
            <input type="checkbox" value="Artificial Intelligence" v-model="names">
          </div>

          <div class="submit">
            <button>Creat An Account</button>
          </div>
        </form>
        <div>
          <p>Email: {{ email }}</p>
          <p>Password: {{ password }}</p>
          <p>Role: {{ role }}</p>
          <p>Terms: {{ terms }}</p>
          <p>Familiarities: {{ names }}</p>
        </div>
    </div>
</template>

<script>
  export default {
      data() {
        return {
          email: '',
          password: '',
          role: 'designer',
          terms: 'false',
          names: [],
          tempSkill: '',
          skills: [],
          passwordError: ''
        }
      },
      methods: {
        addSkill(e) {
          if (e.key === ',' && this.tempSkill){
            if (!this.skills.includes(this.tempSkill)) {
              this.skills.push(this.tempSkill)
            }
            this.tempSkill = ''
          }
        },
        deleteSkill(skill) {
          this.skills = this.skills.filter((item) => {
            return skill !== item
          })
        },
        handleSubmit() {
          this.passwordError = this.password.length > 7 ? '':'Password must be at least 8 characters'
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
    color: #aaa;
    display: inline-block;
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
  .pill {
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
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