<script lang="ts" setup>
import { computed } from 'vue'

interface Props {
    /** 圆角大小，单位：rpx */
    borderRadius?: number
    /** 显示关闭按钮，默认false */
    showClose?: boolean
    /** 显示遮罩，默认true */
    showMask?: boolean
    /** 点击遮罩关闭，默认true */
    maskClosable?: boolean
    /** 显示控制，默认false */
    modelValue?: boolean,
    /** 方向 */
    direction?: 'top' | 'right' | 'bottom' | 'left'
    /** 宽度/高度，默认 200rpx */
    length?: number
    /** 关闭图标，参考：https://zh.uniapp.dcloud.io/component/uniui/uni-icons.html */
    closeIcon?: string
    /** 关闭前处理，返回 true 允许关闭，否则不可关闭 */
    closeBefore?: () => boolean,
    /** 标题 */
    title?: string
}

const props = withDefaults(defineProps<Props>(), {
    borderRadius: 20,
    showClose: false,
    showMask: true,
    maskClosable: true,
    modelValue: false,
    direction: 'bottom',
    length: 200,
    closeIcon: 'closeempty',
    title: '',
    closeBefore: () => { return true }
})

const emit = defineEmits(['update:modelValue', 'close'])

function handleMaskClose() {
    if (props.maskClosable) {
        handleClose()
    }
}

function handleClose() {
    if (props.closeBefore()) {
        emit('update:modelValue', false)
        emit('close')
    }
}


const classes = computed(() => {
    return [
        'y-drawer__content',
        `y-drawer__content-${props.direction}`
    ]
})

</script>

<template>
    <view class="y-drawer" :class="{ active: modelValue }" @touchmove.stop>
        <view class="y-drawer__mask" v-if="showMask" @tap="handleMaskClose" />
        <view :class="classes" :style="{ '--y-border-radius': borderRadius + 'rpx', '--y-length': length + 'rpx' }">
            <view class="y-drawer__close" v-if="showClose" @tap.stop="handleClose">
                <uni-icons :type="closeIcon" :size="22" color="#999"></uni-icons>
            </view>

            <view v-if="title" class="y-drawer__title">{{ title }}</view>

            <slot />

        </view>
    </view>
</template>


<style lang="scss">
@import './y-drawer.scss';
</style>
