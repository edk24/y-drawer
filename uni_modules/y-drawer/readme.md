# y-drawer

> 抽屉组件，仅支持 Vue3

## Example

> 示例

```vue
<template>
  <y-drawer
    :borderRadius="20"
    :showClose="true"
    :showMask="true"
    :maskClosable="true"
    v-model="drawerVisible"
    direction="bottom"
    :length="300"
    title="示例标题"
  >
    <!-- 在这里插入内容 -->
    <view>抽屉内容</view>
  </y-drawer>
</template>

<script lang="ts" setup>
import { ref } from 'vue';
const drawerVisible = ref(false);

setTimeout(() => {
    drawerVisible.value = true
}, 1000);
</script>
```

## Props

> 参数

| 参数名称       | 类型                              | 默认值       | 描述                                       |
| ------------ | --------------------------------- | ---------- | ---------------------------------------- |
| borderRadius | number                            | 20          | 圆角大小，单位：rpx                          |
| showClose    | boolean                           | false      | 显示关闭按钮，默认false                     |
| showMask     | boolean                           | true       | 显示遮罩，默认true                          |
| maskClosable | boolean                           | true       | 点击遮罩关闭，默认true                       |
| modelValue   | boolean                           | false      | 显示控制，默认false                         |
| direction    | 'top' \| 'right' \| 'bottom' \| 'left' | 'bottom'   | 方向                                       |
| length       | number                            | 200        | 宽度/高度，默认 200rpx                       |
| closeIcon    | string                            | 'closeempty' | 关闭图标，参考：<https://zh.uniapp.dcloud.io/component/uniui/uni-icons.html> |
| closeBefore  | () => boolean                     | () => true | 关闭前处理，返回 true 允许关闭，否则不可关闭    |
| title        | string                            | ''         | 标题                                       |

## Slot

> 插槽

| name | 作用   |
| ---- | ---- |
| default | 自定义抽屉内容 |

## End

> 结尾

若在使用过程中发现 BUG，请与我反馈，不胜感激。
