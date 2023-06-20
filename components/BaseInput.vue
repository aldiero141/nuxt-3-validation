<script setup>
import { useField } from "vee-validate";

const props = defineProps({
  name: { type: String, required: true },
  type: { type: String, required: true, default: "text" },
});
const { value, errorMessage } = useField(props.name);
</script>

<template>
  <div class="flex flex-col h-14 w-full">
    <input
      v-model="value"
      :name="props.name"
      :type="props.type"
      placeholder="Type something"
      class="border rounded px-2 py-1 outline-none"
      :class="{
        'border-red-600': !!errorMessage,
        'border-blue-600': !errorMessage,
      }"
    />
    <span class="text-red-600">{{ errorMessage }}</span>
  </div>
</template>
