<script setup lang="ts">

import type { IWeekDay } from '@/models/IWeekDay';
import { defineProps } from 'vue';

//Defino propiedades que recibira del padre(Dia de tipo IWeekDay)
const props=defineProps<{dia:IWeekDay}>()

//Funcion para cambiar clase segun si el dia esta seleccionado
const seleccionado = (select:boolean):string => {
    if (select) {
        return "p-2 m-2 border-3 rounded-sm bg-emerald-500"
    }else{
        return "p-2 m-2 border-3 rounded-sm bg-amber-50"
    }
}

</script>

<template>
    <div v-bind:class="seleccionado(props.dia.selected)" >
        <h2 class="text-gray-800">{{ props.dia.name }}</h2>
    </div>
</template>