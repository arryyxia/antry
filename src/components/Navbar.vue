<template>

	<nav class="z-10 h-20 w-full fixed p-5 lg:px-20 flex justify-between items-center shadow-md bg-white transition-all ease-in-out">
		<a href="#home">
			<img height="80" width="80" src="https://antryofficial.com/logoantry.webp" alt="Logo Antry">
		</a>

		<div class="hidden lg:flex gap-10">
			<a 
				v-for="item in useStore.navItems" 
				:key="item.label" 
				:href="item.to"
				class="hover:text-orange-500 border-b-2 border-white hover:border-orange-500 duration-300 transition-all ease-in-out text-gray-700"
			>
				{{ item.label }}
			</a>
		</div>

		<div class="flex">
			<a href="#daftar" class="bg-orange-500 p-4 hidden lg:flex rounded-full text-white text-center border-2 border-white hover:bg-white hover:border-orange-500 hover:text-orange-500 ease-in-out transition-all">Daftar Sebagai Mitra</a>
			<Button class="flex lg:hidden" icon="pi pi-bars" aria-label="Navigation Button" @click="openPosition('topright')"  />
		</div>
	</nav>

	<Dialog v-model:visible="visible" header="Menu Navigasi" :style="{ width: '25rem', height: '100%', maxHeight: '100%', margin: '0', border: '0' }" :position="position" :modal="true" :draggable="false" class="rounded-none">
		<div class="flex flex-col justify-between h-full">
			<div class="flex flex-col gap-4 ">
				<a
					v-for="item in useStore.navItems" 
					:key="item.label" 
					:href="item.to"
					class="duration-300 ease-in-out transition-all hover:bg-orange-50 hover:text-orange-500 text-center py-5 rounded-md"
					@click="closeDialog"
				>
					{{ item.label }}
				</a>
				<a href="#daftar" class="bg-orange-500 p-5 rounded-full text-white text-center border-2 border-white hover:bg-white hover:border-orange-500 hover:text-orange-500 ease-in-out transition-all" @click="closeDialog">Daftar Sebagai Mitra</a>
			</div>
		</div>
	</Dialog>

</template>

<script>
import { useStore } from '@/stores';

export default {
    name: 'Navbar',
    data() {
        return {
			useStore: useStore(),
			position: 'center',
			visible: false
        };
    },
    methods: {
        openPosition(position) {
            this.position = position;
            this.visible = true;
        },
        closeDialog() {
            this.visible = false;
        }
    }
}
</script>
