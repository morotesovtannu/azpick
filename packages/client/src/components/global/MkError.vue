<template>
<transition :name="$store.state.animation ? 'zoom' : ''" appear>
	<div class="mjndxjcg">
		<img src="https://aozora.uk/assets/innutsu_rie.png" class="_ghost"/>
		<p><i class="fas fa-exclamation-triangle"></i> {{ i18n.ts.somethingHappened }}</p>
		<MkButton class="button" @click="() => $emit('retry')">{{ i18n.ts.retry }}</MkButton>
	</div>
</transition>
</template>

<script lang="ts" setup>
import MkButton from '@/components/MkButton.vue';
import { i18n } from '@/i18n';
</script>

<style lang="scss" scoped>
.mjndxjcg {
	padding: 32px;
	text-align: center;

	> p {
		margin: 0 0 8px 0;
	}

	> .button {
		margin: 0 auto;
	}

	> img {
		vertical-align: bottom;
		height: 128px;
		margin-bottom: 16px;
		border-radius: 16px;
	}
}
</style>
