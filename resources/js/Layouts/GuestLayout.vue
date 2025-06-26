<script setup>
import { Link } from "@inertiajs/inertia-vue3";
</script>

<template>
    <section 
    class="bg-cover bg-center py-20 lg:py-[225px]"
    style="background-image: url('/images/adminlogin_bg.jpg');">
        <div class="container mx-auto">
            <div class="-mx-4 flex flex-wrap">
                <div class="w-full px-4">
                    <div
                    class="relative mx-auto max-w-[525px] overflow-hidden rounded-lg bg-white bg-opacity-50 backdrop-blur-md py-16 px-10 text-center sm:px-12 md:px-[60px]"
                    >
                        <div class="mb-10 text-center md:mb-16">
                            <a
                                class="mx-auto inline-block max-w-[250px] text-3xl font-bold text-gray-800 font-serif"
                            >
                                LIBRARY MANAGEMENT SYSTEM
                            </a>
                        </div>
                        
                        <slot/>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>
