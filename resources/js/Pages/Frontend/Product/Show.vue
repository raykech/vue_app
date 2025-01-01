<template>

    <Head title="Show Products" />

    <FrontendLayout>

        <div class="mt-4 mx-4">
            <div class="flex justify-between">
                <h5>Show Product</h5>
                <Link :href="route('products.index')" class="bg-red-600 text-white p-3 inline-block mb-4">Back</Link>
            </div>


            <div class="grid grid-cols-12 gap-4">
                <div class="mb-3">
                    <label for="name" class="form-label">Name</label>
                    <p>
                        {{ product.name }}
                    </p>
                </div>
                <div class="mb-3">
                    <label for="price" class="form-label">Price</label>
                    <p>
                        {{ product.price }}
                    </p>
                </div>
            </div>

        </div>


    </FrontendLayout>
</template>

<script setup>
import FrontendLayout from '@/Layouts/FrontendLayout.vue';
import { Head, Link } from '@inertiajs/vue3';

const props = defineProps({
    errors: Object,
    product: Object
});

</script>