<script>
import { ref } from "vue";
export default {
  setup() {
    let open = ref(false);
    let links = [
      { name: "Home", links: "/" },
      { name: "Create Item", links: "/create" },
      { name: "All Items List", links: "/list" },
    ];
    function openMenu() {
      open.value = !open.value;
    }
    return { links, open, openMenu };
  },
};
</script>
<template lang="">
  <div class="bg-[#016A70] shadow">
    <div class="mx-auto max-w-7xl py-3.5 px-6">
      <div class="text-gray-100 md:flex justify-between items-center">
        <div>
          <img class="w-20" src="../images/logo.png" alt="logo" />
        </div>
        <div
          @click="openMenu()"
          class="md:hidden absolute right-8 top-6 cursor-pointer duration-700 ease-in"
        >
          <i
            :class="
              open
                ? 'fa-solid fa-xmark text-3xl'
                : 'fa-sharp fa-solid fa-bars text-3xl'
            "
          ></i>
        </div>
        <div>
          <ul
            class="md:flex md:items-center md:space-x-4 space-y-8 md:space-y-0 absolute md:static bg-[#016A70] shadow md:shadow-none py-12 md:py-0 px-8 md:px-0 w-full md:w-auto top-16 duration-700 ease-in"
            :class="[open ? 'left-0' : 'left-[-100%]']"
          >
            <li v-for="link in links">
              <a class="text-2xl md:text-lg" :href="link.links">{{
                link.name
              }}</a>
            </li>
            <li>
              <a
                class="border border-slate-500 rounded px-3 py-1 shadow bg-slate-700 text-2xl md:text-lg"
                href="/getstarted"
              >
                Get Started
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>
