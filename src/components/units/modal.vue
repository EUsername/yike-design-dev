<template>
  <div>
    <Button @click="visible = true">打开</Button>
    <Modal :visible="visible" title="我是标题数据">
      <template #title>
        我是标题数据
      </template>
      hi Im jason
    </Modal>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const visible = ref<boolean>(true)
</script>

<style scoped>

</style>
