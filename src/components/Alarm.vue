<script setup>
const props = defineProps({
    medicineName: String,
    nextDoseTime: String,
    dosageInterval: String,
    isTaken: Boolean,
});
</script>

<template>
    <div
        class="flex items-center justify-around min-w-full py-6 rounded-xl"
        style="
            box-shadow: 0.8rem 0.8rem 1.4rem var(--greyLight-2),
                -0.2rem -0.2rem 1.8rem var(--white);
        "
    >
        <div class="flex justify-center py-2 text-2xl">
            {{ props.medicineName }}
        </div>

        <div class="flex flex-col justify-center py-2 text-2xl">
            <span>{{ props.nextDoseTime }}</span>
            <span class="text-sm">{{ props.dosageInterval }}</span>
        </div>

        <div class="flex justify-center py-2 text-2xl">
            <label>
                <input type="checkbox" :checked="props.isTaken" />
            </label>
        </div>
    </div>
</template>
