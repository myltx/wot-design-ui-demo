<script lang="ts" setup>
import { useQueue, useToast } from 'wot-design-uni'

const { closeOutside } = useQueue()

const select = ref(null)

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
function handleSelect() {
  select.value?.open()
}
</script>

<template>
  <view class="px-3 text-center">
    <view class="my-20px">
      修改后代码
    </view>
    <view @click.stop="closeOutside">
      <wd-swipe-action>
        <wd-cell title="基本用法" value="内容" clickable @click="handleSelect" />
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

      <wd-select-picker ref="select" v-model="value" label="基本用法" :columns="columns" use-default-slot @change="handleChange" />
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
