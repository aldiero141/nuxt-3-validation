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
import * as yup from "yup";

const schema = yup.object({
  username: yup
    .string()
    .required("Username is required")
    .matches(/^[a-zA-Z0-9]*$/g, "This field must be valid (ex.AA0000)"),
  password: yup.string().required("Password is required").min(8),
});

const { handleSubmit } = useForm({
  validationSchema: schema,
});

const submit = handleSubmit((values) => {
  console.log({ values });
  alert("Success Sign-in");
});
</script>
