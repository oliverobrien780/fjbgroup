<template>
  <section class="py-20">
    <div
      class=" items-center max-w-6xl px-4 px-10 mx-auto sm:px-20 md:px-32 lg:px-16"
    >
      <div class="container flex flex-wrap items-center ">
        <div class="order-1 w-full px-3 lg:w-1/2 lg:order-0">
          <div class="w-full lg:max-w-md">
            <h2
              class="mb-4 text-3xl font-bold leading-tight tracking-tight sm:text-4xl font-heading"
            >
              Total Value Locked
            </h2>
            <p class="mb-4 font-medium tracking-tight text-gray-400 xl:mb-6">
              TVL across all modules of $FJB
            </p>
            <ul>
              <li class="flex items-center py-2 space-x-4 xl:py-3">
                <svg
                  class="w-8 h-8 text-pink-500"
                  fill="none"
                  stroke="currentColor"
                  viewBox="0 0 24 24"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M9 3v2m6-2v2M9 19v2m6-2v2M5 9H3m2 6H3m18-6h-2m2 6h-2M7 19h10a2 2 0 002-2V7a2 2 0 00-2-2H7a2 2 0 00-2 2v10a2 2 0 002 2zM9 9h6v6H9V9z"
                  ></path>
                </svg>
                <span class="text-3xl font-medium text-gray-500">
                  100% BNB
                </span>
              </li>
            </ul>
          </div>
        </div>
        <div class="w-full mb-8 lg:w-1/2 order-0 lg:order-1 lg:mb-0">
          <img
            class="mx-auto sm:max-w-sm lg:max-w-full"
            src="../assets/tvl.jpg"
            alt="tvl image"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { defineComponent } from "@vue/composition-api";
import { ethers } from "ethers";
import config from "../utils/config.json";

import tokenAbi from "../utils/token.json";
import routerAbi from "../utils/router.json";

var provider = new ethers.providers.JsonRpcProvider(
  "https://bsc-dataseed.binance.org/"
);

const token = new ethers.Contract(
  config.TOKEN_CONTRACT_ADDRESS,
  tokenAbi,
  provider
);
const router = new ethers.Contract(
  config.PANCAKE_ROUTER_CONTRACT_ADDRESS,
  routerAbi,
  provider
);
import { onMounted, reactive } from "vue";
import { formatEther, parseEther } from "ethers/lib/utils";
export default defineComponent({
  setup() {
    const state = reactive({
      lpLocked: 0,
    });

    onMounted(async () => {
      let wbnbBal = 1;
      try {
        const amountsOut = await router.getAmountsOut(parseEther("1.0"), [
          config.TOKEN_CONTRACT_ADDRESS,
          config.WBNB_ADDRESS,
        ]);

        wbnbBal = parseFloat(formatEther(amountsOut[1])).toFixed(8);
      } catch (e) {
        console.log(e);
      }

      try {
        const totalTokenSupply = await token.totalSupply();
        let totalSupply = parseFloat(formatEther(totalTokenSupply)).toFixed(
          0
        );
        state.lpLocked = parseFloat(0.75 * wbnbBal * totalSupply).toFixed(2);
      } catch (e) {
        console.log(e);
      }
    });

    return { state };
  },
});
</script>
