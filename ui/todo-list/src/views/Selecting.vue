<template>
  <div id="selecting">
    <h2>Option 1</h2> Only one can be selected
    <!--<ul>-->
      <!--<li v-for="item in items" :class="{highlight:item.id == selected}" @click="selected = item.id">{{item.id}}</li>-->
    <!--</ul>-->
    <!--<h2>Option 2</h2> Many can be selected, stores state on item-->
    <!--<ul>-->
      <!--<li v-for="item in items" :class="{highlight:item.selected}" @click="$set(item, 'selected', !item.selected)">{{item.id}}</li>-->
    <!--</ul>-->
    <!--<h2>Option 3</h2> Many can be selected, stores state in separate array-->
    <!--<ul>-->
      <!--<li v-for="item in items" :class="{highlight:selected2.includes(item.id)}" @click="selected2.includes(item.id) ? selected2.splice(selected2.indexOf(item.id), 1) : selected2.push(item.id)">{{item.id}}</li>-->
    <!--</ul>-->
    <h2>Option 4</h2> Hovered
    <ul>
      <li v-for="item in items" :class="{highlight:item.id == selected}" @mouseover="selected = item.id" @mouseout="selected = undefined">{{item.id}}</li>
    </ul>
  </div>
</template>

<script>

  export default {
    name: 'selecting',
    components: {
    },
    data() {
      return {
        items :[],
        selected: undefined,
        selected2: []
      }
    },
    methods: {

    },
    created() {
      for (let i = 1; i <= 10; i++) {
        this.items.push({
          id: i
        })
      }
    }
  }
</script>

<style scoped>
  #selecting {
    box-sizing: border-box;
    margin: 5px;
    padding: 0;
  }

  li:hover {
    color: red;
  }

  li.highlight {
    background: yellow;
  }

  h2 {
    margin-bottom: 0px;
  }

</style>
