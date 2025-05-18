<template>
	<div class="flex flex-col min-h-[100vh] w-full">
		<Header :pages="pages" :title="config.name" @navigate="navigate"></Header>
		<router-view v-slot="{ Component, route}">
            <component :is="Component" @navigate="navigate" :activities="config.activities" :description="config.description" :medias="config.medias" :title="config.title" :contacts="config.contacts" :pages="config.pages" :links="config.links"></component>
        </router-view>
		<Footer @navigate="navigate" :title="config.name" :pages="config.pages" :medias="config.medias" :contacts="config.contacts" :links="config.links"></Footer>
	</div>
</template>

<script setup>
import Header from "./Header.vue";
import Footer from "./Footer.vue";
import config from "../config.js";
import { useRouter } from "vue-router";

const router = useRouter();
const body = document.body;

if (body) {
    body.setAttribute("data-theme", config.theme);
}
//TODO mettre un theme par defaut au cas où

function navigate(page) {
	router.push({
        name: page,
    });
}

</script>

<style></style>
