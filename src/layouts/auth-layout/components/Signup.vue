<template>
  <div class="flex justify-center items-center min-h-screen dark:bg-gray-900 text-white">
    <div class="border w-full max-w-md p-6 space-y-8 sm:p-8 bg-white rounded-lg shadow-xl dark:bg-gray-800">
      <h2 class="raleway-medium text-start text-4xl font-bold text-gray-900 dark:text-white">
        Sign Up
      </h2>
      <form class="mt-8 space-y-6" action="#" @submit.prevent>
        <div>
          <label for="first_name" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">
            First Name
          </label>
          <input type="text" name="first_name" id="first_name" 
            class="w-full bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" 
            placeholder="Your First Name" required 
          />
        </div>
        <div>
          <label for="last_name" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">
            Last Name
          </label>
          <input type="text" name="last_name" id="last_name" 
            class="w-full bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" 
            placeholder="Your Last Name" required 
          />
        </div>
        <div>
          <label for="email" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">
            Gmail
          </label>
          <input type="email" name="email" id="email" 
            class="w-full bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" 
            placeholder="name@company.com" required 
          />
        </div>
        <div>
          <label for="password" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">
            Password
          </label>
          <input type="password" name="password" id="password" 
            class="w-full bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" 
            placeholder="••••••••" required 
          />
        </div>
        <div>
          <label class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">
            Select Role
          </label>
          <div class="flex space-x-4 justify-start">
            <div
              v-for="role in roles"
              :key="role"
              :class="[
                'border p-4 rounded-lg cursor-pointer flex flex-col items-center transition duration-300',
                applying_as === role ? 'border-black bg-gray-50-50 dark:bg-green-900' : 'border-gray-300 dark:border-gray-600'
              ]"
              @click="applyRole(role)"
              role="button"
              tabindex="0"
              @keydown.enter.space="applyRole(role)"
            >
              <span class="font-semibold text-center text-gray-900 dark:text-white">
                {{ role }}
              </span>
            </div>
          </div>
        </div>
        <div class="flex items-center justify-between">
          <div class="flex items-center">
            <input id="remember" aria-describedby="remember" name="remember" type="checkbox" 
              class="w-4 h-4 border-gray-300 rounded bg-gray-50 focus:ring-3 focus:ring-blue-300 dark:focus:ring-blue-600 dark:bg-gray-700 dark:border-gray-600" 
            />
            <label for="remember" class="ml-2 text-sm font-medium text-gray-500 dark:text-gray-400">
              Agree with <router-link to="" class="text-blue-800 font-bold">Privacy</router-link> and <router-link to="" class="text-blue-800 font-bold">Policy</router-link>
            </label>
          </div>
        </div>
        <div class="flex justify-center">
          <button type="submit" 
            class="w-full px-4 py-2 text-base font-medium text-center text-white bg-blue-700 rounded-lg hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
            Signup
          </button>
        </div>
        <div class="text-sm font-medium text-gray-900 dark:text-white text-center">
          Not registered yet? 
          <router-link to="/auth/signin" class="text-blue-600 hover:underline dark:text-blue-500">Create account</router-link>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "Signup",
  setup() {
    const applying_as = ref('');
    const roles = ['Buyer', 'Seller'];
    
    const applyRole = (role) => {
      applying_as.value = role;
    };

    return {
      roles,
      applying_as,
      applyRole,
    };
  },
});
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap');
.raleway-medium {
  font-family: "Raleway", sans-serif;
  font-weight: 600;
}
</style>
