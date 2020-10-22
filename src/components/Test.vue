<template>
  <div class="hello">
    <div>
      <h1>Test Menu</h1>
      <div class="item-wrapper">
        <div
          v-for="item in items"
          :key="item"
          @click.prevent.stop="handleClick($event, item)"
          class="item-wrapper__item"
        >
          {{ item }}
        </div>

        <vue-simple-context-menu
          :elementId="'myUniqueId'"
          :options="menuItems"
          :ref="'vueSimpleContextMenu'"
          @option-clicked="optionClicked"
        />
      </div>
    </div>
  </div>
</template>

<script>
import VueSimpleContextMenu from "vue-simple-context-menu";
import "vue-simple-context-menu/dist/vue-simple-context-menu.css";

export default {
  name: "test",
  components: {
    VueSimpleContextMenu,
  },
  data() {
    return {
      items: ["item1", "itme2", "item3"],
      menuItems: [
        {
          name: "New Contact",
          slug: "new-contact",
        },
        {
          type: "divider",
        },
        {
          name: "New Person Smart List",
          slug: "new-person-smart-list",
        },
      ],
    };
  },
  methods: {
    handleClick(event, item) {
      this.$refs.vueSimpleContextMenu.showMenu(event, item);
    },
    optionClicked(event) {
      window.alert(JSON.stringify(event));
    },
  },
};
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
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
