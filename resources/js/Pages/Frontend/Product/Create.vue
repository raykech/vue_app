<template>

    <Head title="Create Products" />

    <FrontendLayout>
        <div class="mt-4 mx-4">
            <div class="flex justify-between">
                <h5>Product Create</h5>
                <Link :href="route('products.index')" class="bg-red-600 text-white p-3 inline-block mb-4">Back</Link>
            </div>

            <form @submit.prevent="saveProduct()" class="form">
            <div class="grid grid-cols-12 gap-4">
                <div class="mb-3">
                    <label for="name" class="form-label">Name</label>
                    <input type="text" class="py-1 w-full" id="name" v-model="form.name">
                    <div v-if="errors.name" class="text-red-500">{{ errors.name }}</div>
                </div>
                <div class="mb-3">
                    <label for="price" class="form-label">Price</label>
                    <input type="text" class="py-1 w-full" id="price" v-model="form.price">
                    <div v-if="errors.price" class="text-red-500">{{ errors.price }}</div>
                </div>
                <div class="mb-3">
                    <button type="submit" :disabled="form.processing" class="bg-blue-500 text-white py-2 px-5 rounded mb-4">
                        <span v-if="form.processing">Save...</span>
                        <span v-else>Save</span>
                    </button>
                </div>
            </div>
        </form>
        </div>


    </FrontendLayout>
</template>

<script setup>
import FrontendLayout from '@/Layouts/FrontendLayout.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

defineProps({
    errors: Object
});

const form = useForm({
    name: '',
    price: ''
});

const saveProduct = () => {
  const res=  form.post(route('products.store'));
  if(res){
    form.reset();
  }
}
</script>