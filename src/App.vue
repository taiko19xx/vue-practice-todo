<template>
    <div id="app">
      <b-container>
        <header class="mt-2 mb-2">
          <h1>Todo</h1>
        </header>
        <div class="mb-2">
          <b-form-input class="w-25" v-model="newtask" v-on:keyup.enter.native="add"></b-form-input>
        </div>
        <div>
          <b-list-group class="w-25" v-for="(item, index) in items" :key="item.task">
            <a v-on:click="click(index)" v-if="item.completed"><b-list-group-item><del>{{ item.task }}</del></b-list-group-item></a>
            <a v-on:click="click(index)" v-else><b-list-group-item>{{ item.task }}</b-list-group-item></a>
          </b-list-group>
        </div>
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
