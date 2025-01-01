<template> 

    <Head title="Products" />
    
    <FrontendLayout>
      
      <div v-if="$page.props.flash.message" class="alert bg-green-500 text-white p-3 rounded mb-4">
        {{ $page.props.flash.message }}
        </div>

      <div class="mt-4 mx-4">
        <div class="flex justify-between">
          <h5>Product Lists</h5>
          <Link :href="route('products.create')" class="bg-blue-500 text-white p-3 rounded mb-4">Add Product</Link>
        </div>
      </div>
        
      <table class="w-full bg-whit border border-gray-200 shadow">
        <thead>
          <tr>
            <th class="px-4 py-2 text-left border">ID</th>
            <th class="px-4 py-2 text-left border">Name</th>
            <th class="px-4 py-2 text-left border">Price</th>
            <th class="px-4 py-2 text-left border">Action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="product in products.data" :key="product.id">
            <td class="px-4 py-2 border">{{ product.id }}</td>
            <td class="px-4 py-2 border">{{ product.name }}</td>
            <td class="px-4 py-2 border">{{ product.price }}</td>
            <td class="px-4 py-2 border">
              <Link :href="route('products.show', product.id)" class="bg-green-500 text-white p-2 rounded">Show</Link>
              <Link :href="route('products.edit', product.id)" class="bg-blue-500 text-white p-2 rounded">Edit</Link>
              
                <button type="submit" @click="deleteProduct(product.id)" class="bg-red-500 text-white p-2 rounded">Delete</button>
             
            </td>
          </tr> 
        </tbody>
      </table>
        <div class="float-end"><Pagination class="mt-4" :links="products.links" /></div>
      
      </FrontendLayout>
</template>

<script setup>
import FrontendLayout from '@/Layouts/FrontendLayout.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';
import Pagination from '@/Components/Pagination.vue';

defineProps({
  products:[Object, Array],
});

const form = useForm({});

const deleteProduct = (productid) => {
  if (confirm('Are you sure you want to delete this product?')) {
    form.delete(route('products.destroy', productid));
  }
}
</script>