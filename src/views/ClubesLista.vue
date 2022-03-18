<template>
      <v-simple-table>
    <template v-slot:default>
      <thead>
        <tr>
          <th colspan="2" class="text-left">
            Clubes
          </th>
          <th class="text-rigth">
            Pontos
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(clube, index) of clubesListaOrdenada" :key="clube.id">
            <td>{{index + 1}}</td>
            <td>
                <v-avatar size="24px">
                    <img 
                    :src= "clube.escudo"
                    :alt= "clube.nome"
                    >
                </v-avatar>
            
            <span class="pl-2">{{clube.nome}}</span> 
            </td>

        <td>{{clube.pontos}}</td>
        </tr>
      </tbody>
    </template>
  </v-simple-table>
</template>

<script>
export default {
  name: 'ClubesLista',
  data() {
    return {
      clubesLista: []
    }
  },
  computed: {
      clubesListaOrdenada(){
          const listaOrdenada = this.clubesLista.slice(0).sort(
              (a,b) => a.pontos > b.pontos ? -1 : 1 
          );
          return listaOrdenada;
      }
  },

  created() {
    fetch('https://hackthon-decola.firebaseio.com/clubes-lista.json')
      .then(response => response.json())
      .then(json => {
        this.clubesLista = json;
        console.log(this.clubesLista)
      })
  }
}
</script>