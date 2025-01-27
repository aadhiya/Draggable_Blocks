<template>
  <div id="app">
    <h1>Draggable Text Box</h1>

    <!-- Draggable Component -->
    <VueDraggable v-model="blocks" :group="{ name: 'blocks' }">
      <div v-for="(block, index) in blocks" :key="index" class="block">
        <textarea v-if="block.type === 'text'" v-model="block.text" class="block-text"></textarea>
        <button @click="removeBlock(index)">Remove</button>
      </div>
    </VueDraggable>

    <!-- Save Button -->
    <button @click="saveData">Save</button>
  </div>
</template>

<script>

import VueDraggable from 'vue-draggable-plus';  // Import draggable component

export default {
  name: 'App',
  components: {
    VueDraggable
  },
  data() {
    return {
      blocks: [{ type: 'text', text: 'This is a draggable text block' }]  // Initial block data
    };
  },
  methods: {
    removeBlock(index) {
      this.blocks.splice(index, 1); // Removes the block from the array
    },
    saveData() {
      console.log(JSON.stringify(this.blocks)); // Logs the blocks data in JSON format
    }
  }
};
</script>

<style scoped>
.block {
  border: 1px solid #ccc;
  padding: 10px;
  margin: 10px;
  display: flex;
  flex-direction: column;
}

.block-text {
  width: 100%;
  height: 100px;
}

button {
  margin-top: 10px;
}
</style>
