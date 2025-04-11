<script lang="ts" setup>
const value = ref<any>('')

function updateValue() {
  value.value = null
}
</script>

<template>
  <view class="px-3 py-20 text-center">
    <wd-textarea v-model="value" show-word-limit :maxlength="500" placeholder="请填写评价" />
    <!-- <view>
      value: {{ typeof value }}: {{ value }}
    </view> -->
    <wd-button @click="updateValue">
      更新Value为null
    </wd-button>
    <wd-button class="mt-3" @click="value = ''">
      重置Value为空
    </wd-button>
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
