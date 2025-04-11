<script lang="ts" setup>
const value = ref<any>('')
setTimeout(() => {
  value.value = null
}, 1000)
</script>

<template>
  <view class="px-3 py-20 text-center">
    <wd-textarea v-model="value" show-word-limit :maxlength="500" placeholder="请填写评价" />
  </view>
</template>

<route type="home" lang="json">
{
  "name": "home",
  "style": {
    "navigationBarTitleText": "home"
  }
}
</route>
