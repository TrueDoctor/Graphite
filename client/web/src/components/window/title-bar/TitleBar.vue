<template>
	<div class="header-third">
		<WindowButtonsMac :maximized="maximized" v-if="platform === ApplicationPlatform.Mac" />
		<FileMenu v-if="platform !== ApplicationPlatform.Mac" />
	</div>
	<div class="header-third">
		<WindowTitle :title="'X-35B Over Death Valley.gdd* - Graphite'" />
	</div>
	<div class="header-third">
		<WindowButtonsWindows :maximized="maximized" v-if="platform === ApplicationPlatform.Windows || platform === ApplicationPlatform.Linux" />
	</div>
</template>

<style lang="scss">
.header-third {
	display: flex;
	flex: 1 1 100%;

	&:nth-child(1) {
		justify-content: flex-start;
	}

	&:nth-child(2) {
		justify-content: center;
	}

	&:nth-child(3) {
		justify-content: flex-end;
	}
}
</style>

<script lang="ts">
import { defineComponent } from "vue";
import FileMenu from "./FileMenu.vue";
import WindowTitle from "./WindowTitle.vue";
import WindowButtonsWindows from "./WindowButtonsWindows.vue";
import WindowButtonsMac from "./WindowButtonsMac.vue";
import { ApplicationPlatform } from "../MainWindow.vue";

export default defineComponent({
	components: {
		FileMenu,
		WindowTitle,
		WindowButtonsWindows,
		WindowButtonsMac,
	},
	props: {
		platform: { type: String, required: true },
		maximized: { type: Boolean, required: true },
	},
	data() {
		return {
			ApplicationPlatform,
		};
	},
});
</script>
