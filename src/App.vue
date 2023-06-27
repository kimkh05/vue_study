<script>
  import Vue from 'vue';
  import Vuex, { mapState } from 'vuex';
  import 'es6-promise/auto';

  Vue.use(Vuex);

  const store = new Vuex.store({
    state: {
      count: 0,
    },
    mutations: {
      increment(state) {
        state.count += 1;
      }
    }
  });

  store.commit('increment');

  console.log(store.state.count) // -> 1 

  const Counter = {
    template: `<div>{{ count }}</div>`,
    computed: {
      count() {
        return this.$store.state.count;
      }
    }
  };

  const app = new Vue({
    el: '#app',
    store,
    components: { Counter },
    template: `
      <div class="app">
        <counter></counter>
      </div>
    `,
  });


export default {
  name: 'App',
  computed: mapState({
    count: state => state.count,

    countAlias: 'count',

    countPlusLocalState(state) {
      return state.count + this.localCount;
    }
  }),
  methods: {
    increment() {
      this.$store.commit('increment');
    }
  }
}
</script>

<template>
  <div id="app">
    <h1>Vue.js + Vuex</h1>
    <p>{{ count }}</p>
    <button @click="increment">Increment</button>
  </div>
</template>

<style></style>

