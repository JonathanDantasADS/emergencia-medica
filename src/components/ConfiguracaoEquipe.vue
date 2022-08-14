<template>
  <div>
    <div class="row">
      <div class="col">
        <h5><i class="bi-boxes me-2"></i>{{ tituloCustomizadoLocal }}</h5>
      </div>
    </div>
    <div class="row">
      <div class="col-8">
        <p>Enfermeiro: {{ equipe.enfermeiro }}</p>
        <p>Socorrista: {{ equipe.socorrista }}</p>
        <p>Médico: {{ equipe.medico }}</p>
        <p>Carro: {{ equipe.carro }}</p>
        <p>Telefone: {{ equipe.telefone }}</p>
        <p>Kit de reanimação: {{ equipe.kitsDeReanimacao }}</p>
      </div>
      <div class="col-4 text-center">
        <div class="row">
          <div class="col">
            <img class="img-fluid" :src="require('@/assets/ambulancias/indefinida.png')">
          </div>
        </div>
        <div class="row mt-3">
          <div class="col">
            <button 
              type="button" 
              class="btn btn-primary" @click="montarEquipe">
              Montar equipe
            </button>
          </div>
        </div>              
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
    name: 'ConfiguracaoEquipe',
    data: () => ({
      titulo: 'Configuração da equipe',
    }),


    // computed: mapState(['equipe'])
    // computed: {
    //   e() {
    //     return this.$store.state.equipe
    //   }
    // }
    computed: 
    mapState({
      equipe: state => state.equipe,

      // Usando propriedades local e global concatenadas
      tituloCustomizadoLocal(state) {
        return `${this.titulo} : ${state.equipe.carro}`
      }
    }),
    methods: {
      montarEquipe(){
        let equipe = Object.assign({}, this.$store.state.equipe)
        this.$store.commit('adicionaraEquipeEmEquipes', equipe)
      }
    }
}
</script>
