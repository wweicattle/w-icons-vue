<template>
  <div class="icon-show-contain">
    <component
      :is="iconAttr.iconComponent"
      v-if="Object.keys(iconAttr.iconComponent).length > 0"
      :key="Date.now()"
      :color="iconAttr.color"
      :width="iconAttr.width || '170px'"
      :spin="iconAttr.spin"
    >
    </component>
  </div>
</template>

<script setup>
import { computed } from 'vue'
import { useUserStore } from '@/store'

const store = useUserStore()

// 获取选中组件信息
const iconAttr = computed(() => {
  return store.getIconsAttr
})

defineProps({
  visble: {
    type: Boolean,
    default: false
  },
  iconComponent: {
    type: Object
  },
  attrProps: {
    type: Object
  }
})
</script>

<style lang="less" scoped>
.icon-show-contain {
  position: relative;
  background-image: linear-gradient(
      45deg,
      #efefef 25%,
      hsla(0, 0%, 94%, 0) 0,
      hsla(0, 0%, 94%, 0) 75%,
      #efefef 0,
      #efefef
    ),
    linear-gradient(45deg, #efefef 25%, hsla(0, 0%, 94%, 0) 0, hsla(0, 0%, 94%, 0) 75%, #efefef 0, #efefef);
  height: 100%;
  background-color: #fff;
  background-position: 0 0, 10px 10px;
  background-size: 20px 20px;
  svg {
    width: 170px;
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    margin: auto;
  }
}
</style>
