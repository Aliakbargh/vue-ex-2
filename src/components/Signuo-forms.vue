<template>
  <h1>aliakbar</h1>
  <form @submit.prevent="handler">
    <label>email: </label>
    <input type="email" required v-model="email" />

    <label>password: </label>
    <input type="password" required v-model="pass" />

    <label>role :</label>
    <select v-model="role">
      <option value="developer">developer</option>
      <option value="designer">designer</option>
    </select>

    <label>skills: </label>
    <input type="text" @keypress.enter="addSkill" v-model="tempSkills" />
    <div v-for="skill in skills" :key="skill">
      <span @click="removeSkill(skill)">{{ skill }}</span>
    </div>
    <button style="text-align: center;" > submit </button>
  </form>
  <!-- 
    <div class="checkbox">
      <label>mamad</label>
      <input type="checkbox" value="mamad" v-model="mamadCheckbox" />
    </div>

    <div class="checkbox">
      <label>aliakbar</label>
      <input type="checkbox" value="aliakbar" v-model="arrayOfCheckbox" />

      <label>alireza</label>
      <input type="checkbox" value="aliareza" v-model="arrayOfCheckbox" />

      <label>ali</label>
      <input type="checkbox" value="ali" v-model="arrayOfCheckbox" />
    </div>-->

  <p>email : {{ email }}</p>
  <p>password : {{ pass }}</p>
  <p>role : {{ role }}</p>

  <!-- <p>check : {{ mamadCheckbox }}</p>
  <p>arrayCheck : {{ arrayOfCheckbox }}</p> -->
</template>

<script>
export default {
  data() {
    return {
      email: "",
      pass: "",
      role: "designer",
      mamadCheckbox: false,
      arrayOfCheckbox: [],
      tempSkills: "",
      skills: [],
    };
  },
  methods: {
    addSkill() {
      if (this.tempSkills) {
        if (!this.skills.includes(this.tempSkills)) {
          this.skills.push(this.tempSkills);
          this.tempSkills = "";
        } else {
          this.tempSkills = "";
        }
      }
    },
    removeSkill(skill) {
      this.skills = this.skills.filter((item) => {
        return skill != item;
      });
    },
    handler(){
        console.log("ananans")
    }
  },
};
</script>

<style>
form {
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: center;
  padding: 40px;
  border-radius: 20px;
}

label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
  font-size: 0.6rem;
}
input,
select {
  display: block;
  padding: 20px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #bbb;
  color: #555;
}
</style>