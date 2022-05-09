<template>
  <Form @submit="submit" :validation-schema="schema" v-slot="{ errors }">
    <Field name="email" />
    <span>{{ errors.email }}</span>
    <Field name="password" type="password" rules="required|min:8" />
    <span>{{ errors.password }}</span>
    <button>Submit</button>
  </Form>
</template>
<script>
import { Form, Field } from 'vee-validate';
export default {
  components: {
    Form,
    Field,
  },
  data() {
    const schema = {
      email: { required: true },
      password: { required: true, between: [0, 10] },
    };
    return {
      schema,
    };
  },
};
</script>