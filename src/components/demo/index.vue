<template>
  <div>
    <p class="color_pink">{{ msg }}</p>
    <p class="color_pink">{{ id }}</p>
    <p class="color_pink">{{ title }}</p>
    <slot name="btnChild"></slot>
    <slot name="btnChild1"></slot>
    <el-button type="danger" @click="Btn">子组件</el-button>

  </div>
</template>

<script lang="ts" setup>

const props = defineProps({
  fatherMsg: {
    type: String,
    default: 'fathermsg'
  },
  id: {
    type: Number,
    default: 0
  },
  title: {
    type: String,
    default: ''
  }
});
const msg = computed(() => { return props.fatherMsg })
const emit = defineEmits(['myBtnChild'])

watch(props, (news, olds) => {
  console.log('子组件watch', news, olds)
})
const fontSize = reactive({ color: 'pink' });
function Btn() {
  console.log('子组件')
  emit('myBtnChild', '子组件触发传值')
}
</script>
<style lang="less" scoped>
.color_pink {
  color: v-bind('fontSize.color');
}
</style>
