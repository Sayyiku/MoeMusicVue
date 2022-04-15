<template>
  <div class="login-page">
    <div class="title">MoeMusic</div>
    <q-card class="login-form-content">
      <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
        <q-input
          filled
          v-model="name"
          label="Your name *"
          hint="Name and surname"
          lazy-rules
          :rules="[val => (val && val.length > 0) || 'Please type something']"
        />

        <q-input
          filled
          type="password"
          v-model="age"
          label="Your password *"
          lazy-rules
          :rules="[
            val => (val !== null && val !== '') || 'Please type your password',
            val => (val > 0 && val < 100) || 'Please type a real password'
          ]"
        />

        <q-toggle v-model="accept" label="I accept the license and terms" />

        <div>
          <q-btn
            class="full-width"
            label="Login"
            type="submit"
            color="primary"
          />
        </div>
      </q-form>
    </q-card>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'Login',
  setup() {
    const accept = ref(false);
    return { accept };
  }
};
</script>

<style scoped lang="less">
.login-page {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  .title {
    font-size: 2rem;
    font-weight: 500;
    margin-bottom: 1rem;
  }

  .login-form-content {
    width: 400px;
    padding: 20px;
  }
}
</style>
