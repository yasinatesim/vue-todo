<template>
  <div id="app">
    <div class="container">
      <!-- Not found area -->
      <NotFound :items="items" />

      <!-- Items -->
      <Items :items="items" />

      <!-- Form -->
      <Form :label="label" :value="label" @input="label = $event" />
    </div>
  </div>
</template>

<script>
// Containers
import Items from '@/containers/items';

// Components
import Form from '@/components/form';
import NotFound from '@/components/not-found';

export default {
  name: 'App',
  components: {
    Items,
    Form,
    NotFound
  },
  data() {
    return {
      label: '',
      items: []
    };
  },
  methods: {
    add() {
      this.items.push({
        label: this.label,
        completed: false
      });

      this.label = '';
    },

    remove(itemIndex) {
      this.items.splice(itemIndex, 1);
    },

    completed(itemIndex) {
      const item = this.items[itemIndex];
      item.completed = !item.completed;
    }
  }
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

input:focus,
button:focus {
  outline: 0;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
}

ul {
  list-style: none;
}

.container {
  width: 50%;
  margin-left: auto;
  margin-right: auto;
  box-shadow: 2px 2px 20px rgba(0, 0, 0, 0.2);
  border-radius: 6px;
  padding: 20px;
  margin-top: 100px;
}
</style>
