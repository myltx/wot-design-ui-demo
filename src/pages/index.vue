<script lang="ts" setup>
import { useQueue, useToast } from 'wot-design-uni'
import Fix from './fix.vue'

const { closeOutside } = useQueue()

const toast = useToast()

function handleAction(action: string) {
  toast.show(`点击了${action}`)
}
const columns = ref<Record<string, any>>([
  {
    value: '101',
    label: '男装',
  },
  {
    value: '102',
    label: '奢侈品',
  },
  {
    value: '103',
    label: '女装',
  },
])
const value = ref<string[]>(['101'])

function handleChange({ value }) {
  toast.show(`选择了${value}`)
}
</script>

<template>
  <view class="px-3 py-20 text-center">
    <view @click.stop="closeOutside">
      <view class="my-20px">
        嵌套
      </view>
      <wd-swipe-action>
        <wd-select-picker v-model="value" label="基本用法" :columns="columns" @change="handleChange" />
        <template #right>
          <view class="action">
            <view class="button" style="background: #C8C7CD;" @click="handleAction('操作1')">
              操作1
            </view>
            <view class="button" style="background: #FFB300;" @click="handleAction('操作2')">
              操作2
            </view>
            <view class="button" style="background: #E2231A;" @click="handleAction('操作3')">
              操作3
            </view>
          </view>
        </template>
      </wd-swipe-action>

      <view class="my-20px">
        非嵌套
      </view>
      <wd-select-picker v-model="value" label="基本用法" :columns="columns" @change="handleChange" />

      <view class="my-20px">
        view嵌套
      </view>
      <view>
        <wd-select-picker v-model="value" label="基本用法" :columns="columns" @change="handleChange" />
      </view>

      <Fix />
    </view>
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
