<script setup>
import AnalogClock from "./components/AnalogClock.vue";
import Alarm from "./components/Alarm.vue";
</script>

<template>
  <div class="container flex justify-center mx-auto mt-16">
    <div class="flex flex-col items-center">
      <AnalogClock />
    </div>
  </div>

  <div class="container flex justify-center mx-auto mt-16">
    <div class="flex items-center justify-around min-w-full text-gray-500">
      <span class="text-xl">Remédio</span>
      <span class="text-xl">Horário</span>
      <span>Já tomado</span>
    </div>
  </div>

  <div class="container flex justify-center mx-auto mt-6">
    <div class="flex flex-col items-center min-w-full">
      <Alarm
        medicineName="Paracetamol"
        nextDoseTime="12:00:00 AM"
        dosageInterval="a cada 8 horas"
        isTaken
      />
    </div>
  </div>
</template>
