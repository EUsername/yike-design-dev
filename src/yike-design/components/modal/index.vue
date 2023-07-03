<template>
  <teleport to="body">
    <div class="yk-modal-wrap" v-if="state.modalVisible">
    <div class="yk-modal">
      <div class="yk-modal-header">
        <template v-if="title">
          {{ title }}
        </template>
        <slot name="title" v-else />
        <Icon name="yk-cha" class="yk-modal-close" />
      </div>
      <div class="yk-modal-content">
        <slot />
      </div>
      <div class="yk-modal-footer">
        <Space>
          <Button type="sceondary" @click="cencel">次要按钮</Button>
          <Button type="outline">线框按钮</Button>
        </Space>
      </div>
    </div>
  </div>
  </teleport>
  
</template>

<script setup lang="ts">
import { reactive, toRefs, watch } from 'vue';

const props = defineProps({
  visible: {
    type: Boolean,
    default: false
  },
  title: {
    type: String,
    default: '',
  },
  width: {
    type: Number,
    default: 0
  },
  confirm: {
    type: Function
  }
})
const state = reactive({
  modalVisible: props.visible
})

const confirm = () => {
  state.modalVisible = false
}
const cencel = () => {
  state.modalVisible = false
}






</script>

<style scoped lang="less">
@import '../../assets/style/yk-index.less';
.yk-modal-wrap {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: col;
  justify-content: center;
  align-items: center;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 999;
  background: #00000040;
  font-weight: 400;
  .yk-modal {
    width: 33%;
    border-radius: .5rem;
    background-color: @bg-color-l;
    .yk-modal-header {
      font-size: 16px;
      padding: 12px 20px;
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 1px 0 0 @line-color-s;
      .yk-modal-close {
        width: 18px;
        height: 18px;
        padding: 2px;
        background-color: @bg-color-s;
      }
    }
    .yk-modal-content {
      padding: 20px;
      
    }
    .yk-modal-footer {
      padding: 20px;
      display: flex;
      flex-direction: row;
      justify-content: end;
      box-shadow: 0 -1px 0 0 @line-color-s;

    }
  }
}
</style>