<script setup>
import { ref } from "vue";
import { Link } from "@inertiajs/inertia-vue3";
import Notice from "@/Components/Notice.vue";

const showingNavigationDropdown = ref(false);
const showMenu = ref(false);
</script>

<template>
    <div>
        <nav class="bg-white shadow-lg">
            <div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
                <div class="relative flex h-16 items-center justify-between">
                    <div
                        class="absolute inset-y-0 left-0 flex items-center sm:hidden">
                    </div>
                 <div class="flex flex-1 items-center ">
                    <Link
                      :href="route('dashboard')"
                       class="text-xl font-bold flex items-center lg:ml-2.5" >
                       <span
                         class="text-2xl font-bold font-serif text-gray-800">
                         Library Management System
                       </span>
                    </Link>
                        <div class="hidden sm:ml-6 sm:block">
                            <div class="flex space-x-4">
                                <Link
                                    :href="route('student.dashboard')"
                                    class="hover:bg-gray-700 hover:text-white px-3 py-2 rounded-md text-sm font-medium"
                                    :class="{active: $page.url.startsWith('/student/dashboard'),}"
                                    aria-current="page"
                                    >Dashboard
                                </Link>
                                
                                

                                <Link
                                    :href="route('search.book')"
                                    class="hover:bg-gray-700 hover:text-white px-3 py-2 rounded-md text-sm font-medium"
                                    :class="{active: $page.url.startsWith('/student/search'),}"
                                    >Search Book
                                </Link>
                            </div>
                        </div>
                    </div>
                    <div
                        class="absolute inset-y-0 right-0 flex items-center pr-2 sm:static sm:inset-auto sm:ml-6 sm:pr-0">
                        <button
                            type="button"
                            class="rounded-full bg-gray-800 p-1 text-gray-400 hover:text-white focus:outline-none focus:ring-2 focus:ring-white focus:ring-offset-2 focus:ring-offset-gray-800">
                            <span class="sr-only">View notifications</span>
                            <svg
                                class="h-6 w-6"
                                xmlns="http://www.w3.org/2000/svg"
                                fill="none"
                                viewBox="0 0 24 24"
                                stroke-width="1.5"
                                stroke="currentColor"
                                aria-hidden="true">
                                <path
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                    d="M14.857 17.082a23.848 23.848 0 005.454-1.31A8.967 8.967 0 0118 9.75v-.7V9A6 6 0 006 9v.75a8.967 8.967 0 01-2.312 6.022c1.733.64 3.56 1.085 5.455 1.31m5.714 0a24.255 24.255 0 01-5.714 0m5.714 0a3 3 0 11-5.714 0"
                                />
                            </svg>
                        </button>

                        <!-- Profile dropdown -->
                        <div class="relative ml-3">
                            <div>
                                <button
                                    type="button"
                                    class="flex rounded-full bg-gray-800 text-sm focus:outline-none focus:ring-2 focus:ring-white focus:ring-offset-2 focus:ring-offset-gray-800"
                                    id="user-menu-button"
                                    aria-expanded="false"
                                    aria-haspopup="true"
                                    @click="
                                        showingNavigationDropdown =
                                            !showingNavigationDropdown">
                                    <span class="sr-only">Open user menu</span>
                                    <img
                                        class="h-8 w-8 rounded-full"
                                        src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                                        alt=""
                                    />
                                </button>
                            </div>

                            <div
                                class="absolute right-0 z-10 mt-2 w-48 origin-top-right rounded-md bg-white py-1 shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none"
                                role="menu"
                                aria-orientation="vertical"
                                aria-labelledby="user-menu-button"
                                tabindex="-1"
                                :class="{ hidden: !showingNavigationDropdown }">

                                <Link
                                    :href="route('student.profile')"
                                    class="block px-4 py-2 text-sm text-gray-700"
                                    role="menuitem"
                                    tabindex="-1"
                                    id="user-menu-item-0"
                                    >Your Profile
                                </Link>

                                <Link
                                    :href="route('student.logout')"
                                    as="button"
                                    type="button"
                                    method="post"
                                    class="block px-4 py-2 text-sm text-gray-700"
                                    role="menuitem"
                                    tabindex="-1"
                                    id="user-menu-item-2"
                                    >Sign out
                                </Link>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </nav>
        <div class="container mx-auto px-10 py-10">
            <Notice />
            <main>
                <slot />
            </main>
        </div>
    </div>
</template>

<style scoped></style>
