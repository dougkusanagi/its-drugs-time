<script setup>
import { ref, onMounted } from "vue";

const hours_pointer = ref(0);
const minutes_pointer = ref(0);
const seconds_pointer = ref(0);

const hours = ref(0);
const minutes = ref(0);
const seconds = ref(0);

const sufix = ref("am");

const clock = () => {
    let today = new Date();
    let h = (today.getHours() % 12) + today.getMinutes() / 59; // 22 % 12 = 10pm
    let m = today.getMinutes(); // 0 - 59
    let s = today.getSeconds(); // 0 - 59

    if (today.getHours() >= 12) {
        sufix.value = "pm";
    }

    hours.value = today.getHours() % 12;
    minutes.value = m.toString().padStart(2, "0");
    seconds.value = s.toString().padStart(2, "0");

    h *= 30; // 12 * 30 = 360deg
    m *= 6;
    s *= 6; // 60 * 6 = 360deg

    rotation(hours_pointer.value, h);
    rotation(minutes_pointer.value, m);
    rotation(seconds_pointer.value, s);

    // call every second
    setTimeout(clock, 500);
};

const rotation = (target, val) => {
    target.style.transform = `rotate(${val}deg)`;
};

onMounted(() => clock());
</script>

<template>
    <div class="clock">
        <div ref="hours_pointer" class="hand hours"></div>
        <div ref="minutes_pointer" class="hand minutes"></div>
        <div ref="seconds_pointer" class="hand seconds"></div>

        <div class="point"></div>

        <div class="marker">
            <span class="marker__1"></span>
            <span class="marker__2"></span>
            <span class="marker__3"></span>
            <span class="marker__4"></span>
        </div>
    </div>

    <p
        class="text-8xl font-bold mt-10 text-[color:var(--primary)] font-['digital-7']"
    >
        {{ hours }}:{{ minutes }}:{{ seconds }} {{ sufix }}
    </p>
</template>
