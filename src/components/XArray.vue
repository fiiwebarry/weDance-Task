<template>
  <div>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        <input v-bind:value="item" v-on:input="updateArray(index, $event.target.value)" />
        <button @click="removeItem(index)">Remove</button>
      </li>
      <li>
        <input v-model="newItem" @keyup.enter="addItem" />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [],
      newItem: '',
    }
  },
  methods: {
    addItem() {
      this.items.push(this.newItem)
      this.newItem = ''
    },
    updateArray(index, item) {
      if (item === '') {
        this.removeItem(index)
      } else {
        this.items.splice(index, 1, item)
      }
    },
    removeItem(index) {
      this.items.splice(index, 1)
    }
  }
}
</script>
