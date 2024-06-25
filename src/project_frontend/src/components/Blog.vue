<template>
    <div>
        <button @click="pobierzWpisy">refresh</button>
        czesc blog ! pozdrfawiam 
        {{ wpisy }}
        <input v-model="nowyBlog" type="text">
        <button @click="dodajWpis">dodaj</button>
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
}
</script>