<script setup lang="ts">
import DayCard from './DayCard.vue';
import type { IWeekDay } from '../models/IWeekDay';
import { ref } from 'vue';

//Creo arreglo de dias como variable reactiva
const days = ref<IWeekDay[]>([
    {
        id:1,
        name:"Lunes",
        selected:false
    },
    {
        id:2,
        name:"Martes",
        selected:false
    },
    {
        id:3,
        name:"Miercoles",
        selected:false
    },
    {
        id:4,
        name:"Jueves",
        selected:false
    },
    {
        id:5,
        name:"Viernes",
        selected:false
    },
    {
        id:6,
        name:"Sabado",
        selected:false
    },
    {
        id:7,
        name:"Domingo",
        selected:false
    }
])

//Funcionalidad para seleccionar dia
const selectDay = (identifier:number):void => {
    days.value.forEach(d => {
        if(d.id === identifier){
            d.selected = true
        }else{
            d.selected = false
        }
    })
}

//Funcionalidad para cambiar clases del dia seleccionado
const seleccionado = (select:boolean):string => {
    if (select) {
        return "lg:w-1/8 sm:w-full text-gray-50 bg-blue-900 border-2 m-2 p-2 rounded-sm"
    }else{
        return "lg:w-1/8 sm:w-full text-blue-900 bg-gray-50 border-2 m-2 p-2 rounded-sm"
    }
}

//Funcionalidad para cancelar seleccion de dia
const cancelSelect = ():void => {
    days.value.forEach(d => {
        d.selected = false
    })
}


</script>

<template>
    <div class="lg:flex sm:flex justify-center flex-wrap">
        <button v-for="dia in days" @click="selectDay(dia.id)" v-bind:class="seleccionado(dia.selected)">{{ dia.name }}</button>
        <button @click="cancelSelect()" class="lg:w-1/8 sm:w-full text-gray-900 bg-red-400 border-2 m-2 p-2 rounded-sm"> Cancelar seleccion</button>
    </div>

    <h3> Listado Dias </h3>
    <div class="lg:flex sm:flex justify-center flex-wrap bg-cyan-200 border-1 rounded-sm">

        <DayCard v-for="dia in days" :dia="dia"  class="lg:w-1/8 sm:w-full"/>
        
    </div>
    

</template>

