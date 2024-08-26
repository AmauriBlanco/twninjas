<script setup>
import { ref } from "vue";
import { RouterLink, RouterView } from "vue-router";

// Estado reativo para controlar a visibilidade do menu
const isMenuOpen = ref(false);

// Função para abrir o menu
const openMenu = () => {
    isMenuOpen.value = true;
};

// Função para fechar o menu
const closeMenu = () => {
    isMenuOpen.value = false;
};
</script>

<template>
    <header id="header" class="bg-[#1C1C1C]">
        <nav
            class="mx-auto flex container items-center justify-between p-6 lg:px-8"
            aria-label="Global"
        >
            <div class="flex lg:flex-1">
                <a href="#" class="-m-1.5 p-1.5">
                    <span class="sr-only">Your Company</span>
                    <img
                        src="img/twninjas-logo.svg"
                        alt="Logo"
                        width="150px"
                    />
                </a>
            </div>

            <!-- Menu Button -->
            <div class="flex lg:hidden">
                <button
                    id="menu-button"
                    type="button"
                    class="-m-2.5 inline-flex items-center justify-center rounded-md p-2.5 text-white"
                    @click="openMenu"
                >
                    <span class="sr-only">Open main menu</span>
                    <svg
                        class="h-6 w-6"
                        fill="none"
                        viewBox="0 0 24 24"
                        stroke-width="1.5"
                        stroke="currentColor"
                        aria-hidden="true"
                    >
                        <path
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5"
                        />
                    </svg>
                </button>
            </div>

            <!-- Desktop Menu -->
            <div
                class="hidden lg:flex lg:gap-6 xl:gap-x-12 text-sm text-white uppercase"
            >
                <RouterLink to="/" class="">Home</RouterLink>
                <RouterLink to="/sobre" class="">sobre</RouterLink>
                <RouterLink to="/servicos" class=""
                    >lista de serviços</RouterLink
                >
                <RouterLink to="/contato" class="">contato</RouterLink>
            </div>
        </nav>

        <!-- Mobile menu, show/hide based on menu open state. -->
        <div
            id="mobile-menu"
            class="lg:hidden"
            role="dialog"
            aria-modal="true"
            v-show="isMenuOpen"
        >
            <div class="fixed inset-0 z-10 bg-black/50"></div>
            <div
                class="fixed inset-y-0 right-0 z-10 w-full overflow-y-auto bg-[#1C1C1C] px-6 py-6 sm:max-w-sm sm:ring-1 sm:ring-white/10"
            >
                <div class="flex items-center justify-between">
                    <a href="#" class="-m-1.5 p-1.5">
                        <span class="sr-only">Your Company</span>
                        <img
                            class="h-20 w-auto"
                            src="img/twninjas-logo.svg"
                            alt="Logo"
                        />
                    </a>
                    <button
                        id="close-menu"
                        type="button"
                        class="-m-2.5 rounded-md p-2.5 text-gray-400"
                        @click="closeMenu"
                    >
                        <span class="sr-only">Close menu</span>
                        <svg
                            class="h-6 w-6"
                            fill="none"
                            viewBox="0 0 24 24"
                            stroke-width="1.5"
                            stroke="currentColor"
                            aria-hidden="true"
                        >
                            <path
                                stroke-linecap="round"
                                stroke-linejoin="round"
                                d="M6 18L18 6M6 6l12 12"
                            />
                        </svg>
                    </button>
                </div>
                <div class="mt-6 flow-root">
                    <div class="-my-6 divide-y divide-gray-500/25">
                        <div
                            class="flex flex-col gap-6 py-6 font-semibold leading-7 text-white hover:bg-gray-800 uppercase text-center sm:text-left"
                        >
                            <RouterLink to="/" class="" @click="closeMenu"
                                >Home</RouterLink
                            >
                            <RouterLink to="/sobre" class="" @click="closeMenu"
                                >sobre</RouterLink
                            >
                            <RouterLink
                                to="/servicos"
                                class=""
                                @click="closeMenu"
                                >lista de serviços</RouterLink
                            >
                            <RouterLink
                                to="/contato"
                                class=""
                                @click="closeMenu"
                                >contato</RouterLink
                            >
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </header>
</template>

<style scoped>
/* Estilos personalizados, se necessário */
</style>
