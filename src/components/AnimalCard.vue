<script setup>
import dayjs from "dayjs";
const props = defineProps({
  animal: Object,
});
function arrivalText(intakeDate) {
  const date = dayjs(intakeDate);
  return `Arrived ${date.format("MMM D, YYYY")} (${dayjs().diff(date, "day")} days ago)`;
}
const emit = defineEmits(["toggle"]);
// App owns the animal data, so the card creates an event instead of changing it directly.
</script>

<template>
  <!-- TODO 2: Build one animal's card. See README.md for the markup. -->

  <article class="animal-card" :class="{ adopted: animal.adopted }">
    <h3>{{ animal.name }}</h3>

    <p>{{ animal.species }}, {{ animal.age }} years old</p>

    <p>{{ arrivalText(animal.intakeDate) }}</p>

    <p>{{ animal.adopted ? "Adopted" : "Available" }}</p>

    <button type="button" @click="emit('toggle')">
      {{ animal.adopted ? "Return" : "Adopt" }}
    </button>
  </article>
</template>
