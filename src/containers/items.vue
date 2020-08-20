<template>
  <ul>
    <li :class="`item ${item.completed ? 'completed' : ''}`" v-for="(item, index) in items" :key="item.index">
      <div :class="`label ${item.completed ? 'completed' : ''}`">
        {{ item.label }}
      </div>
      <div>
        <button class="completed" @click="completed(index)">
          <svg width="18" height="18">
            <g transform="translate(-192.905,-516.02064)">
              <path
                style="fill:#fff"
                d="M 197.67968,534.31563 C 197.40468,534.31208 196.21788,532.53719 195.04234,530.37143 L 192.905,526.43368 L 193.45901,525.87968 C 193.76371,525.57497 194.58269,525.32567 195.27896,525.32567 L 196.5449,525.32567 L 197.18129,527.33076 L 197.81768,529.33584 L 202.88215,523.79451 C 205.66761,520.74678 208.88522,517.75085 210.03239,517.13691 L 212.11815,516.02064 L 207.90871,520.80282 C 205.59351,523.43302 202.45735,527.55085 200.93947,529.95355 C 199.42159,532.35625 197.95468,534.31919 197.67968,534.31563 z "
              />
            </g>
          </svg>
        </button>
        <button class="remove" @click="remove(index)">x</button>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'Items',
  props: {
    items: {
      type: Array,
      required: true
    }
  },
  methods: {
    remove(itemIndex) {
      this.$parent.remove(itemIndex);
    },
    completed(itemIndex) {
      this.$parent.completed(itemIndex);
    }
  }
};
</script>

<style lang="scss" scoped>
// Variables
$completed-button: #16a085;
$remove-button: #c0392b;

.item {
  background-color: #ecf0f1;
  padding: 12px 16px;
  font-size: 14px;
  display: flex;
  align-items: center;
  justify-content: space-between;

  .label {
    font-weight: normal;
    position: relative;
    &::after {
      content: '';
      background-color: #2c3e50;
      width: 0;
      height: 2px;
      position: absolute;
      left: 0;
      top: 50%;
      transition: 500ms all;
    }

    &.completed {
      font-weight: bold;

      &::after {
        width: 100%;
      }
    }
  }

  &:not(:last-child) {
    margin-bottom: 8px;
  }

  & button.remove,
  & button.completed {
    color: #fff;
    cursor: pointer;
    border: 0;
    font-size: 18px;
    margin-left: 10px;
    padding: 12px 16px;
  }

  & button.remove {
    background-color: $remove-button;
    &:hover {
      background-color: darken($remove-button, 10%);
    }
  }

  & button.completed {
    background-color: $completed-button;
    &:hover {
      background-color: darken($completed-button, 10%);
    }
  }
}
</style>
