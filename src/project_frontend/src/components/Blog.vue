<template>
    <div>
        <button @click="pobierzWpisy">refresh</button>
        I H8 Niggers
        {{ wpisy }}
    </div>
</template>

<script>
import { project_backend } from 'declarations/project_backend/index';

export default { 
    data() { 
        return { 
            wpisy: []
        }
    },
    methods: { 
        async pobierzWpisy() { 
           this.wpisy = await project_backend.odczytaj_wpisy()
        }
    },
}
</script>