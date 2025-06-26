<script setup>
import GuestLayout from "@/Layouts/GuestLayout.vue";
import InputError from "@/Components/InputError.vue";
import { Head, Link, useForm } from "@inertiajs/inertia-vue3";

defineProps({
    canResetPassword: Boolean,
    status: String,
});

const form = useForm({
    email: "",
    password: "",
    remember: false,
});

const submit = () => {
    form.post(route("login"), {
        onFinish: () => form.reset("password"),
    });
};
</script>

<template>
    <GuestLayout>
        <Head title="Log in" />

        <div v-if="status" class="mb-4 font-medium text-sm text-green-600">
            {{ status }}
        </div>

        <!-- General login error -->
        <div v-if="form.errors.email && !form.errors.password" class="mb-4 text-sm text-red-600">
            {{ form.errors.email }}
        </div>

    

        <form @submit.prevent="submit">
            <div class="mb-6">
                <input
                    type="text"
                    placeholder="Email"
                    v-model="form.email"
                    class="bordder-[#E9EDF4] w-full rounded-md border bg-[#FCFDFE] py-3 px-5 text-base text-body-color placeholder-[#ACB6BE] outline-none focus:border-primary focus-visible:shadow-none"
                    required
                    autofocus
                    autocomplete="username"
                />
                <InputError class="mt-2" :message="form.errors.email && form.errors.password" />
            </div>
            <div class="mb-6">
                <input
                    type="password"
                    placeholder="Password"
                    class="bordder-[#E9EDF4] w-full rounded-md border bg-[#FCFDFE] py-3 px-5 text-base text-body-color placeholder-[#ACB6BE] outline-none focus:border-primary focus-visible:shadow-none"
                    v-model="form.password"
                    required
                    autocomplete="current-password"
                />
                <InputError class="mt-2" :message="form.errors.password" />
            </div>
            
            <div class="mb-10">
                <input
                    type="submit"
                    value="Login"
                    class="border-transparent w-full cursor-pointer rounded-md border bg-gray-800 py-3 px-5 text-base text-white transition hover:bg-gray-700"
                    :class="{ 'opacity-25': form.processing }"
                    :disabled="form.processing"
                />
            </div>
        </form>
    </GuestLayout>
</template>
