<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    quotes: {
        type: Object,
        required: true
    }
})

</script>

<template>
    <div class="table">
        <thead>

            <tr>
                <th>Código:</th>
                <th>Nome:</th>
                <th>Máximo:</th>
                <th>Minimo:</th>
                <th>Variação:</th>
                <th></th>
            </tr>

        </thead>
        <tbody>

            <tr v-for="(quote, key) in props.quotes" :key="key">

                <td>{{ key }}</td>
                <td>{{ quote.name }}</td>
                <td>{{ quote.high }}</td>
                <td>{{ quote.low }}</td>

                <td>
                    <span
                    class="label label-rounded text-small"
                    :class="{'label-error' : quote.pctChange < 0, 'label-success' : quote.pctChange > 0}"
                    >

                        > {{ quote.pctChange }} %
                    </span>
                </td>


            </tr>

        </tbody>
    </div>
</template>

<style scoped></style>