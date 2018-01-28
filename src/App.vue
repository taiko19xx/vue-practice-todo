<template>
    <div id="app">
      <b-container>
        <h1>Todo</h1>
        <b-form-input v-model="newtask" v-on:keyup.enter.native="add"></b-form-input>
        <b-list-group v-for="(item, index) in items">
          <b-list-group-item v-if="item.completed"><a v-on:click="click(index)"><del>{{ item.task }}</del></a></b-list-group-item>
          <b-list-group-item v-else><a v-on:click="click(index)">{{ item.task }}</a></b-list-group-item>
        </b-list-group>
      </b-container>
    </div>
</template>

<script>
export default {
  name: "app",
  data () {
    return {
      newtask: '',
      items: [
        {task: "doing", completed: false},
        {task: "completed", completed: true}
      ]
    }
  },
  methods: {
    add: function (event) {
      this.items.push({task: this.newtask, completed: false})
      this.newtask = ''
    },
    click: function (index) {
      // this.item.completed = !this.item.completed
      let item = this.items[index]
      item.completed = !item.completed
    }
  },
}
</script>

<style>

</style>
