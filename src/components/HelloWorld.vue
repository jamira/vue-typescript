<template>
  <div class="hello">
    <form @submit.prevent="addUser">
     <ul>
      <li>
        <label for="name">Enter Name:</label>
        <input type="text" placeholder="Enter your name here..." v-model="userDetail.name" />
      </li>
      <li>
        <label for="name">Enter Address:</label>
        <input type="text" placeholder="Enter your address here..." v-model="userDetail.address" />
      </li>
      <li>
        <label for="name">Enter Phone:</label>
        <input type="text" placeholder="Enter your phone here..." v-model="userDetail.phone" />
      </li>
      <li>
        <p>Please select your gender:</p>
        <div v-for="(sex, key) in gender" :key="key">
          <input type="radio" :id="sex" name="gender" :value="sex" v-model="userDetail.gender">
          <label :for="sex">{{ sex }}</label><br>
        </div>
      </li>
     </ul>
     <button type="submit">Add User Detail</button>
    </form>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Emit } from 'vue-property-decorator'
@Component
export default class HelloWorld extends Vue {
  private gender: Array<string> = ['male', 'female'];
  userDetail: Record<string, any> = {
    name: '',
    address: '',
    phone: '',
    gender: ''
  };

  @Emit()
  addUser (): Record<string, any> {
    return this.userDetail
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 10px 0;
}

li:last-child > div {
  display: flex;
}

a {
  color: #42b983;
}

label {
  display: block;
  text-transform: capitalize;
}

.hello {
  width: 50%;
}

input[type=text] {
  width: 100%;
  box-sizing: border-box;
  padding: 0.5em;
}

p {
  margin: 5px 0;
}
</style>
