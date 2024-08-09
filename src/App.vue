<script setup>
import cot from './components/cot.vue';
import api from './serve/api';
import { onMounted, reactive, toRefs } from 'vue';


const data = reactive({ 
  quotes: {},

})
const { quotes } = toRefs(data);

onMounted(async () => {
  const response = await api.all()
  data.quotes = response.data
})

</script>

<template>
  <div class="container grid-lg my-2  py-2 card1">
    <div class="card">

      <div class="card-header">

        <div class="h4 text-center">Exibindo moedas</div>

      </div>

      <div class="card-body">
        <cot :quotes="quotes" />
      </div>

    </div>
  </div>
</template>

<style scoped>
.card1 {

  align-items: center;
  display: flex;
  align-items: center;
  justify-content: center;
}

@media ((min-width: 320px) and (max-width: 426px)) {
  .card {
    font-size: 10px;
    gap: 0;
    margin-left: 20px;

  }
}

.h4 {
  margin-bottom: 10px;
}

.card {
  box-shadow: inset 0 0 1em gold, 0 0 1em red;
}
</style>
