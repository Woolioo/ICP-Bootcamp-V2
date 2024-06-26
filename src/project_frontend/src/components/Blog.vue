<template>
    <div class=" ">
        <h2 class="text-green-700">Wpisy na bloga: </h2>

        <div class="w-100 flex flex-row justify-center">
            <button @click="pobierzWpisy" class="bg-green-600 rounded-md text-white p-2 hover:bg-white hover:text-green-600  transition duration-500 ease-in-out border-2 border-white hover:border-green-600">refresh</button>
        </div>
        <div class="grid mx-6 gap-4 my-4">
            <div v-for="wpis in wpisy" class="drop-shadow-xl bg-stone-200">
            <p>{{ wpis }}</p>
        </div>
        </div>
       
        <input v-model="nowyBlog" type="text">
        <button @click="dodajWpis" class="bg-green-600 rounded-md text-white p-2 hover:bg-white hover:text-green-600  transition duration-500 ease-in-out border-2 border-white hover:border-green-600">dodaj</button>
    </div>
</template>

<script>
import { project_backend } from 'declarations/project_backend/index';

export default { 
    data() { 
        return { 
            wpisy: [],
            nowylog: ""
        }
    },
    methods: { 
        async dodajWpis() { 
            await project_backend.dodaj_wpis(this.nowyBlog);
        },

        async pobierzWpisy() { 
           this.wpisy = await project_backend.odczytaj_wpisy();
        }
    },
    async mounted() { 
        this.pobierzWpisy()
    }
}
</script>