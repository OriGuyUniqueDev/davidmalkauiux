<template>
	<div ref="elementWidth" class="mainWrapper md:w-[80rem] md:mx-auto flex flex-col mx-4 mb-8 lg:flex-row lg:h-[40rem] lg:w-[128rem] lg:mb-[8.8rem] lg:gap-[14.7rem] ">
			<div class=" ">
				<RouterLink class="w-full" :to="{ name: 'project', params: { id: title } }">
					<div :class="[bgCard]" class=" rounded-[2rem] overflow-hidden h-max-[40rem] sm:h-[40rem] md:w-[80rem] md:h-[40rem] lg:w-[56.4rem] 2xl:w-[69rem]">
					<img :class="[scale,hoverScale]" :src="url" :alt="alt" class=" " /></div>
				</RouterLink>
				
			</div>
		<div class="textButtonWrapper flex justify-between lg:flex-col lg:justify-evenly my-4">
			<div>
				<h1 class="text-[900] text-[4.8rem] leading-[6.398rem]">{{ title }}</h1>
				<h2 class="text-greyText text-[3.2rem] leading-[4.032rem]">{{ role }}</h2>
			</div>
			<RouterLink :to="{ name: 'project', params: { id: title } }">
				<button v-if="width >= 550" type="button" class="self-center w-[14.6rem] h-[4.5rem] lg:self-start">View project </button>
			</RouterLink>
		</div>
	</div>
</template>

<script setup>
	import { ref } from "vue";
	import { useElementSize } from "@vueuse/core";
	import { useMotion } from "@vueuse/motion";
	const props = defineProps(["title", "role", "url", "alt",'bgCard','scale','hoverScale']);
	let elementWidth = ref(null);
	const { width } = useElementSize(elementWidth);
	const motionInstance = useMotion(elementWidth, {
		initial: {
			opacity: 0,
		},
		visibleOnce: {
			opacity: 1,
			transition: {
				duration: 500,
			},
		},
	});
</script>

<style scoped>
	/* .titleToHide {
		display: none;
	} */
	 div > .titleToHide{
		display: none;
	 }

	 div:hover > .titleToHide {
		display: block;
	}
	img {
		transition: all 0.375s linear;
	}
	h1 {
		font-family: "Playfair Display", serif;
	}
	h2 {
		font-family: "Outfit", sans-serif;
	}
	button {
		background: linear-gradient(96.02deg, #ff1392 -1.37%, #7b3ce1 46.36%, #10a9ff 95.6%);
		border: 0;
		width: 14.6rem;
		height: 4.5rem;
		position: relative;
		border-radius: 999px;
		z-index: 6;
		transition: 0.3s all ease-out;
	}
	div {
		transition: 0.3s all ease-out;
	}
	button::before {
		content: "View Project";
		font-family: "Outfit", sans-serif;
		padding-block: 0.9rem;
		/* letter-spacing: 5%; */
		/* line-height: 3.3rem; */
		font-size: 1.6rem;
		display: block;
		position: absolute;
		top: 1px;
		left: 1px;
		width: calc(100% - (1px * 2));
		height: calc(100% - (1px * 2));
		background-color: #1b1b1b;
		border-radius: 999px;
		transition: 0.3s all ease-out;
	}
	button:hover::before {
		content: "View Project";
		font-family: "Outfit", sans-serif;
		padding-block: 0.9rem;
		/* letter-spacing: 5%; */
		/* line-height: 3.3rem; */
		font-size: 1.6rem;
		display: block;
		position: absolute;
		top: 1px;
		left: 1px;
		width: calc(100% - (1px * 2));
		height: calc(100% - (1px * 2));
		background-color: #323232;
		border-radius: 999px;
		transition: 0.3s all ease-out;
	}
</style>
