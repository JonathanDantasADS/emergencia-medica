<template>
    <div>
        <ul class="list-group">
            <li 
                class="list-group-item" 
                v-for="(equipe, indice) in equipes" 
                :key="indice">
                    <equipe :dados="equipe"/>
            </li>
        </ul>
    </div>
</template>

<script>
import Equipe from '@/components/Equipe'
import { mapState } from 'vuex'

export default {
    name: 'ListaEquipes',
    components: {
        Equipe
    },
    computed: {
        ...mapState(['equipes']
        )
    }
}
</script>