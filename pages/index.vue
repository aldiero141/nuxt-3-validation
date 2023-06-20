<template>
  <div class="flex flex-col w-[20vw]">
    <form @submit.prevent="submit">
      <div>
        <label for="username">Username</label>
        <BaseInput name="username" type="text" />
      </div>
      <div>
        <label for="password">Password</label>
        <BaseInput name="password" type="password" />
      </div>
      <button
        class="bg-blue-700 px-2 py-2 rounded text-white w-full mt-4"
        type="submit"
      >
        Sign-in
      </button>
    </form>
  </div>
</template>

<script setup lang="ts">
import { useForm } from "vee-validate";

function validateUsername(value: string) {
  if (!value) {
    return "This field is required";
  }
  const regex = /^[a-zA-Z0-9]*$/g;
  if (!regex.test(value)) {
    return "This field must be valid (ex.AA0000)";
  }
  return true;
}

function validatePassword(value: string) {
  if (!value) {
    return "this field is required";
  }
  return true;
}

const simpleSchema = {
  username: validateUsername,
  password: validatePassword,
};

const { handleSubmit } = useForm({
  validationSchema: simpleSchema,
});

const submit = handleSubmit((values) => {
  console.log({ values });
  alert("Submit Form");
});
</script>
