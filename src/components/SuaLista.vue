<script lang="ts">
import type {PropType} from "vue";
import Tag from "@/components/Tag.vue";

export default {
  components: { Tag },
  props: {
    ingredientes: { type: Array as PropType<string[]>, required: true }
  }
}

</script>

<template>
  <section>
      <span class="subtitulo-lg sua-lista-texto">
        Sua lista:
      </span>
    <ul v-if="ingredientes.length" class="ingredientes-sua-lista">
      <!--   v-for = diretiva do vue  -->

      <!--v-bind é uma diretiva do vue que atribui um identificador único para cada item -->
      <!--Assim:  v-bind:key="ingrediente" -->
      <!--Ou Assim:        :key="ingrediente"-->

      <li v-for="ingrediente in ingredientes" v-bind:key="ingrediente">
        <Tag :texto="ingrediente" ativa/>
      </li>
    </ul>

    <p v-else class="paragrafo lista-vazia">
      <img src="../assets/images/icones/lista-vazia.svg" alt="ícone de pesquisa">
      Sua lista está vazia, selecione ingredientes para iniciar.
    </p>
  </section>
</template>

<style scoped>
.lista-vazia {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.25rem;

  color: var(--coral, #F0633C);
  text-align: center;
}

.sua-lista-texto {
  color: var(--coral, #F0633C);
  display: block;
  text-align: center;
  margin-bottom: 1.5rem;
}

.ingredientes-sua-lista {
  display: flex;
  justify-content: center;
  gap: 1rem 1.5rem;
  flex-wrap: wrap;
}
</style>