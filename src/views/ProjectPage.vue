<template>
	<div class="w-full ">
		<ProjectHero  :bgColor1="data.bgColor" :topImage="data.topImage"></ProjectHero>
		<div class="px-[1.8rem] md:px-[12rem] xl:px-[20rem] ">
			<div fieldName="about" class="mb-20">
				<h1 class="text-bold mt-8 text-[3.2rem]">{{ data.projectTitle }}</h1>
				<p class="text-[1.6rem] lg:w-[50%]">{{ data.details }}</p>
			</div>
			<div fieldName="personas" class="mb-[10.8rem]">
				<h2 class="text-white text-bold mt-8 text-[3.2rem] mb-[2rem]">{{ data.secondTitle }}</h2>
				<Personas v-for="persona in data.secondTitleDetails" :icon="persona.icon" :data="persona.data"></Personas>
			</div>
			<div fieldName="research" class="mb-[10.8rem] relative">
				<h2 class="text-white text-bold mt-8 text-[3.2rem] mb-[2rem]">{{ data.thirdTitle }}</h2>
				<ResearchComponent v-for="card in data.thirdTitleDetails" :icon="card.icon" :data="card.data"></ResearchComponent>
			</div>
			<div fieldName="slider" class="mb-[10.8rem]">
				<h2 class="text-white text-bold mt-8 text-[3.2rem] mb-[2rem]">Paint Points</h2>
				<Slider :cards="data.fourthTitleDetails"></Slider>
			</div>
			<div fieldName="challenges" class="mb-[5rem] lg:w-[100%] xl:flex xl:flex-col">
				<h2 class="text-white mt-8 text-[3.2rem] mb-[2rem]">{{ data.fifthTitle }}</h2>
				<Challenges v-for="challenge in data.fifthTitleDetails" :challengeData="challenge"></Challenges>
			</div>
			<div fieldName="bottom pic" class="flex flex-col md:-ml-[13.8rem] xl:-ml-[21.8rem] w-[100vw]">
				<img class="
				w-[100%] scale-125 my-20
				md:scale-x-125 
				xl:scale-[1]
				" :src="data.pic2" alt="" />
				<img class="
				w-[42.9rem] scale-x-105 my-0 mx-auto
				md:w-[91.5rem] md:scale-x-100
			
				" :src="data.pic3" alt="" />
			</div>
			<hr class="bg-dividers relative left-[-1.8rem] md:left-[-12rem] xl:left-[-20rem]  w-[100vw] h-[2px]">
			<div fieldName="buttons" class="relative -ml-[1.8rem] md:-ml-[13.8rem] xl:-ml-[21.8rem] w-[100vw]">
				<div class="flex flex-row justify-between md:justify-evenly md:gap-128 bg-black px-[2.2rem] py-4">
					<RouterLink :to="{ name: 'project', params: { id: data.btnPre } }">
						<div class="btnWrapper flex flex-col gap-[1.5rem] w-40">
							<p class="text-[1.4rem]">Previous project</p>
							<button>
								<img class="mx-auto" src="/icons/leftArrow.svg" alt="left arrow" />
							</button>
						</div>
					</RouterLink>
					<RouterLink :to="{ name: 'project', params: { id: data.btnFor } }">
						<div class="btnWrapper flex flex-col gap-[1.5rem] w-40">
							<p class="text-[1.4rem] mx-auto">Next project</p>
							<button>
								<img class="mx-auto" src="/icons/rightArrow.svg" alt="left arrow" />
							</button>
						</div>
					</RouterLink>
				</div>
			</div>
		</div>
		<hr class="bg-dividers h-[2px]">
		<div ref="target" class="toAnimate relative ">
			<Footer></Footer>
			<!-- <Developer></Developer> -->
		</div>
	</div>
</template>

<script setup>
	import ProjectHero from "../components/ProjectHero.vue";
	import Personas from "../components/Personas.vue";
	import ResearchComponent from "../components/ResearchComponent.vue";
	import Slider from "../components/Slider.vue";
	import Challenges from "../components/Challenges.vue";
	import { onUpdated } from "vue";
	import { useRouter } from "vue-router";
import HomepageHiddenComponent from "../components/HomepageHiddenComponent.vue";
import Footer from "../components/Footer.vue";
	const router = useRouter();

	let props = defineProps(["id", "data"]);
	const emit = defineEmits(["updateNav"]);

	onUpdated(() => {
		emit("updateNav", props.id);
	});
</script>

<style scoped>
	h1,
	h2 {
		color: white;
		font-family: "Playfair Display";
		font-weight: 900;
	}
	p {
		color: white;
		font-family: "Outfit";
		font-weight: 300;
	}
</style>
