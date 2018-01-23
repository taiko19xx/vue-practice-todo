<template>
    <div id="app">
      <input v-model="newtask" v-on:keyup.enter="add">
      <ul>
        <li v-for="(item, index) in items">
          <span v-if="item.completed"><a v-on:click="click(index)"><del>{{ item.task }}</del></a></span>
          <span v-else><a v-on:click="click(index)">{{ item.task }}</a></span>
        </li>
      </ul>
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
