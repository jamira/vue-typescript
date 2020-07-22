<template>
  <div class="items" v-if="data.length">
    <h3>User List</h3>
    <table>
      <tr>
        <th>Action</th>
        <th>Name</th>
        <th>Address</th>
        <th>Phone</th>
        <th>Gender</th>
      </tr>
      <tr v-for="(item, key) in data" :key="key">
        <td>
          <span @click="onEdit(key)">Edit</span>
          <span @click="onDelete(key)">Delete</span>
        </td>
        <td v-text="item.name"></td>
        <td v-text="item.address"></td>
        <td v-text="item.phone"></td>
        <td v-text="item.gender"></td>
      </tr>
    </table>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue, Emit } from 'vue-property-decorator'

@Component
export default class ListItems extends Vue {
 @Prop() readonly data!: Array<object>;

 @Emit()
 onEdit (key: number): number {
   return key
 }

 @Emit()
 onDelete (key: number): number {
   return key
 }

 get formattedData (): Array<object> {
   return this.data.map((item: any) => {
     return {
       'Full Name': item.name,
       'Current Address': item.address,
       'Contact Number': item.phone,
       Gender: item.gender
     }
   })
 }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}

.items {
  width: 50%;
}

span {
  margin-right: 10px;
}
</style>
