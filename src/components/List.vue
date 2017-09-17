<template>
  <div>
    <div class="col-6 category" v-for="category in list" v-bind:key="category.name">
      <h3>{{ category.verbose }}</h3>
      <ul>
        <li v-for="(item, index) in category.items" v-bind:key="item.name">
          <input type="checkbox" :name="item.name" :id="item.name" v-model="item.status">
          <label :for="item.name">{{item.verbose}}</label>
        </li>
      </ul>
    </div>
    <button class="btn btn-info" v-on:click="print()">Imprimir</button>
    <button class="btn btn-danger" v-on:click="resetData()">Resetar Dados</button>
  </div>
</template>

<script>
import defaultData from '../patterns/default.json'
export default {
  name: 'list',
  components: {

  },
  data () {
    return {
      listKey: 'currentList',
      list: null
    }
  },
  watch: {
    list: {
      handler: function () {
        console.log('watching')
        this.$session.set(this.listKey, this.list)
      },
      deep: true
    }
  },
  methods: {
    resetData () {
      if (confirm('Deseja mesmo resetar o formulário?')) {
        this.$session.clear()
        this.list = defaultData
      }
    },
    print () {
      window.print()
    }
  },
  created () {
    let _list = this.$session.get(this.listKey)
    if (_list) {
      this.list = _list
    } else {
      this.list = defaultData
    }
  }
}
</script>

<style>
  ul {
   padding: 0; 
  }
  ul li {
    list-style-type: none;
  }
</style>

