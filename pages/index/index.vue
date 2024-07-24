<template>
	<view class="content">
		<y-drawer v-model="a" title="11" :showClose="true" :borderRadius="20">
			2222
		</y-drawer>
	</view>
</template>

<script setup>
import { ref } from 'vue';
	const a = ref(false)
	
	setTimeout(() => a.value=true, 3000)
</script>
