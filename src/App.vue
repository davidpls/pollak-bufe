<script setup>
import { ref, computed } from "vue";
import Rightside from "./components/Rightside.vue";
import { RouterView, RouterLink } from "vue-router";

const time = ref(new Date());

setInterval(() => {
  time.value = new Date();
}, 1000);

const getMinutes = computed(() =>
  time.value.getMinutes().toString().padStart(2, "0")
);
const getHours = computed(() =>
  time.value.getHours().toString().padStart(2, "0")
);

function navBack() {
  history.back();
}
</script>

<template>
  <img
    src="./assets/arrow_left.svg"
    alt=""
    class="h-8 w-8 absolute left-2 top-2"
    @click="navBack()"
  />
  <img
    src="./assets/shoppingcart.svg"
    alt=""
    class="h-8 w-8 absolute right-32 top-8"
  />
  <div
    class="h-10 w-20 absolute right-4 top-6 bg-[#F7F2FA] drop-shadow-lg text-3xl flex justify-center items-center rounded-xl font-sans"
  >
    {{ getHours }}:{{ getMinutes }}
  </div>
  <main class="w-screen h-screen bg-[#F5F5F5] flex">
    <div class="w-96 h-full bg-[#D9D9D9]">
      <nav class="h-full p-6">

        <ul class="h-full flex flex-col justify-evenly content-center flex-wrap text-[#6750A4] text-2xl">
          <li class="w-full border-b border-[#D1C0FB] pr-2 pl-2 pb-3">
            <RouterLink to="/szendvicsek" class="flex justify-between w-full">Szendvicsek <img width="20px" src="./assets/arrow_right.svg"
            /></RouterLink>
          </li>

          <li class="w-full border-b border-[#D1C0FB] pr-2 pl-2 pb-3">
            <RouterLink class="flex justify-between w-full" to="/hot-dogok"
              >Hot-dogok <img width="20px" src="./assets/arrow_right.svg"
            /></RouterLink>
          </li>

          <li class="w-full border-b border-[#D1C0FB] pr-2 pl-2 pb-3">
            <RouterLink class="flex justify-between w-full" to="/hamburgerek"
              >Hamburgerek <img width="20px" src="./assets/arrow_right.svg"
            /></RouterLink>
          </li>

          <li class="w-full border-b border-[#D1C0FB] pr-2 pl-2 pb-3">
            <RouterLink class="flex justify-between w-full" to="/italok"
              >Italok <img width="20px" src="./assets/arrow_right.svg"
            /></RouterLink>
          </li>

          <li class="w-full border-b border-[#D1C0FB] pr-2 pl-2 pb-3">
            <RouterLink class="flex justify-between w-full" to="/nasik"
              >Nasik <img width="20px" src="./assets/arrow_right.svg"
            /></RouterLink>
          </li>
        </ul>

      </nav>
    </div>
    <div class="w-full h-screen max-h-screen p-4">
      <RouterView />
    </div>
  </main>
</template>

<style scoped></style>
