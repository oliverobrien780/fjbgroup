<template>
  <div>
    
    <!-- Section 1 -->
    <section class="w-full px-6 pb-12 antialiased bg-white">
      <div class="mx-auto max-w-7xl">
        <img src="../assets/fuckbiden.jpg">
        <!-- Main Hero Content -->
        <div
          class="container max-w-lg px-4 py-40 mx-auto text-left md:max-w-none md:text-center"
        >
          <h1
            class="text-5xl font-extrabold leading-10 tracking-tight text-left text-gray-900 md:text-center sm:leading-none md:text-6xl lg:text-7xl"
          >
            <span><a href="https://t.me/FJBGROUP">FuckJoeBiden</a></span>
          </h1>
          <div
            class="mx-auto mt-5 text-gray-500 md:mt-12 md:max-w-lg md:text-center lg:text-lg"
          >
            is a community driven, fair launched DeFi Token. FuckJoeBiden holders holds the tokens to make Joe Biden regrets his regulations. We are decentralized, not binding by a centralized authority.
          </div>
          <div class="flex flex-col items-center mt-12 text-center">
            <span class="relative inline-flex w-full md:w-auto">
              <a
                href="https://exchange.pancakeswap.finance/#/swap?outputCurrency=0x7909cb6284d299a765Aa9884B4B08196337AF702"
                type="button"
                class="inline-flex items-center justify-center w-full px-8 py-4 text-base font-bold leading-6 text-white bg-green-600 border border-transparent  md:w-auto hover:bg-indigo-500 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-600"
              >
                Buy $FJB Token
              </a>
              <span
                class="absolute top-0 right-0 px-2 py-1 -mt-3 -mr-6 text-xs font-medium leading-tight text-white bg-green-400 rounded-full"
                >PancakeSwap</span
              >
            </span>
            <a
              href="https://bscscan.com/token/0x7909cb6284d299a765Aa9884B4B08196337AF702"
              class="mt-3 text-sm text-green-500"
              >BSCScan</a
            >
          </div>
        </div>
        <!-- End Main Hero Content -->
      </div>
    </section>
  </div>
</template>

<script>
import { defineComponent } from "@vue/composition-api";
import { reactive } from "vue";
export default defineComponent({
  setup() {
    const state = reactive({
      showMenu: false,
    });
    return { state };
  },
});
</script>
