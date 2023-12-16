<template>
  <!--
    <html class="h-full bg-white">
    <body class="h-full">
  -->
  <div
    class="flex min-h-full flex-1 flex-col justify-center px-6 py-12 lg:px-8"
  >
    <div class="sm:mx-auto sm:w-full sm:max-w-sm">
      <img
        class="mx-auto h-10 w-auto"
        src="https://res2.weblium.site/res/64a8412785289b000f9a73e6/64a84363c1d57e000f16374d_optimized_483.webp"
        alt="Your Company"
      />
      <h2
        class="mt-10 text-center text-2xl font-bold leading-9 tracking-tight text-gray-900"
      >
        Увійти до свого кабінету
      </h2>
    </div>

    <div class="mt-10 sm:mx-auto sm:w-full sm:max-w-sm">
      <form
        @submit.prevent="someAction()"
        class="space-y-6"
        action="#"
        method="POST"
      >
        <div class="">
          <label
            for="email"
            class="flex items-start text-sm font-medium leading-6 text-gray-900"
            >Email адрес</label
          >
          <div class="mt-2">
            <input
              v-model="email"
              @blur="isEmailTouched = true"
              :class="{ error: isEmailError }"
              id="email"
              name="email"
              type="email"
              autocomplete="email"
              required="true"
              class="p-4 block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
            />
          </div>
          <div v-if="isEmailError">
            Поле заповнено не вірно
          </div>
        </div>

        <div>
          <div class="flex items-center justify-between">
            <label
              for="password"
              class="block text-sm font-medium leading-6 text-gray-900"
              >Пароль</label
            >
            <div class="text-sm">
              <a
                href="#"
                class="font-semibold text-cyan-500 hover:text-teal-400"
                >Забули пароль?</a
              >
            </div>
          </div>
          <div class="mt-2">
            <input
              v-model="password"
              id="password"
              name="password"
              type="password"
              autocomplete="current-password"
              required="true"
              class="p-4 block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
            />
            <p class="forgetmenot my-2">
              <label for="rememberme"
                ><input
                  name="rememberme"
                  type="checkbox"
                  id="rememberme"
                  value="forever"
                />
                Запам'ятати мене</label
              >
            </p>
          </div>
        </div>

        <div>
          <button
            :disabled="!isEmailValid"
            type="submit"
            class="my-2 flex w-full justify-center rounded-md bg-cyan-500 px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-sky-400 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
          >
            Увійти
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
const emailCheckRegex =
  /^(([^<>()[\].,;:\s@"]+(\.[^<>()[\].,;:\s@"]+)*)|(".+"))@(([^<>()[\].,;:\s@"]+\.)+[^<>()[\].,;:\s@"]{2,})$/;

export default {
  data() {
    return {
      email: null,
      password: null,
      isEmailTouched: false,
    };
  },

  computed: {
    isEmailValid() {
      return emailCheckRegex.test(this.email);
    },

    isEmailError() {
      return !this.isEmailValid && this.isEmailTouched;
    },
  },

  methods: {
    someAction() {
      if (!this.isEmailValid) {
        return;
      }

      alert(this.password);
    },
  },
};
</script>

<style scoped>
.forgetmenot {
  font-weight: 400;
  float: left;
  margin-bottom: 0;
}
.field {
  margin-bottom: 24px;
}

.field > label {
  margin-right: 8px;
}

.error {
  border-color: red;
}
</style>
