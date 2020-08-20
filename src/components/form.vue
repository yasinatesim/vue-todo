<template>
  <form @submit.prevent="add">
    <input type="text" placeholder="What are you doing today?" v-model="value" />
    <button type="submit" :disabled="label.length < 1">Add</button>
  </form>
</template>

<script>
export default {
  name: 'Form',
  props: {
    label: {
      type: String,
      required: true
    }
  },
  methods: {
    add() {
      this.$parent.add();
    }
  },
  computed: {
    value: {
      get() {
        return this.label;
      },
      set(val) {
        this.$emit('input', val);
      }
    }
  }
};
</script>

<style lang="scss">
// Variables
$dark: #34495e;
$light: #fff;

// Mixins
@mixin disabled {
  border-color: #ccc;
  color: #999;
  background: #ccc;
}

form {
  margin-top: 16px;
}

form input {
  display: block;
  border: 2px solid $dark;
  padding: 12px;
  width: 100%;
}

form button {
  margin-top: 16px;
  padding: 12px 16px;
  background-color: $light;
  border: 2px solid $dark;
  cursor: pointer;
  color: $dark;

  &:hover {
    background-color: $dark;
    color: $light;
  }
}

form button:disabled {
  cursor: not-allowed;
  @include disabled;
}
</style>
