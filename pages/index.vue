<template>
  <div class="pv4">
    <article class="pa3 pa5-ns">
      <h1 class="f4 bold center mw6">Todos</h1>
      <ul class="list pl0 ml0 center mw6 ba b--light-silver br2">
        <li v-for="todo of todos"
            class="ph3 pv3 bb b--light-silver">{{todo.task}}</li>
      </ul>
    </article>
  </div>
</template>

<script>
import {
  mapState
} from 'vuex'
import axios from 'axios'
export default {
  async fetch ({ store, redirect }) {
    try {
      let res = await axios.get('https://todos-gfsjbhmsmp.now.sh/todos')
      store.commit('init', res.data)
    } catch (error) {
      redirect('/error')
    }
  },
  computed: {
    ...mapState({
      todos: state => state.todos
    })
  },
  methods: {

  }
}
</script>
