<script setup>
import { reactive, ref } from "@vue/reactivity";
import { computed, onMounted } from "@vue/runtime-core";

const matchesContainer = ref(null);
const showTitleBadge = ref(false);
const strategyList = reactive([
  {
    name: "Price Crosses Up Kumo",
    positionBuy: true,
  },
  {
    name: "RSI Crosses Up 30",
    positionBuy: false,
  },
  {
    name: "MACD Crosses Up SignalLine",
    positionBuy: true,
  },
  {
    name: "RSI Below And Close ToBearish Trendline",
    positionBuy: false,
  },
  {
    name: "RSI Above And Close toBullish Trendline",
    positionBuy: true,
  },
]);

const coinList = reactive([
  {
    name: "btc",
    price: "24,0000",
    pair: "usdt",
    percentage: "7.94",
    imgUrl: "https://cdn.arzdigital.com/uploads/assets/coins/icons/bitcoin.png",
    matchList: [
      {
        id: 1,
        timeframe: ["4h", "1w", "1d"],
        time: "7 hrs ago",
        isMached: true,
      },
      {
        id: 2,
        timeframe: ["4h", "1w", "1d"],
        time: "1 hrs ago",
        isMached: false,
      },
      {
        id: 3,
        timeframe: ["4h", "1w", "1d"],
        time: "7 hrs ago",
        isMached: true,
      },
      {
        id: 4,
        timeframe: ["4h", "1w", "1d"],
        time: "1 day ago",
        isMached: true,
      },
      {
        id: 5,
        timeframe: ["4h", "1w", "1d"],
        time: "1 day ago",
        isMached: false,
      },
    ],
  },
  {
    name: "eth",
    price: "1,0540",
    pair: "usdt",
    percentage: "-5.6",
    imgUrl:
      "https://cdn.arzdigital.com/uploads/assets/coins/icons/ethereum.png",
    matchList: [
      {
        id: 1,
        timeframe: ["4h", "1w", "1d"],
        time: "7 hrs ago",
        isMached: true,
      },
      {
        id: 2,
        timeframe: ["4h", "1w", "1d"],
        time: "1 hrs ago",
        isMached: false,
      },
      {
        id: 3,
        timeframe: ["4h", "1w", "1d"],
        time: "7 hrs ago",
        isMached: true,
      },
      {
        id: 4,
        timeframe: ["4h", "1w", "1d"],
        time: "1 day ago",
        isMached: true,
      },
      {
        id: 5,
        timeframe: ["4h", "1w", "1d"],
        time: "1 day ago",
        isMached: false,
      },
    ],
  },
  {
    name: "usdt",
    price: "0.99965",
    pair: "usdt",
    percentage: "-0.01",
    imgUrl: "https://cdn.arzdigital.com/uploads/assets/coins/icons/tether.png",
    matchList: [
      {
        id: 1,
        timeframe: ["4h", "1w", "1d"],
        time: "7 hrs ago",
        isMached: true,
      },
      {
        id: 2,
        timeframe: ["4h", "1w", "1d"],
        time: "1 hrs ago",
        isMached: false,
      },
      {
        id: 3,
        timeframe: ["4h", "1w", "1d"],
        time: "7 hrs ago",
        isMached: true,
      },
      {
        id: 4,
        timeframe: ["4h", "1w", "1d"],
        time: "1 day ago",
        isMached: true,
      },
      {
        id: 5,
        timeframe: ["4h", "1w", "1d"],
        time: "1 day ago",
        isMached: false,
      },
    ],
  },
  {
    name: "doge",
    price: "24,0000",
    pair: "usdt",
    percentage: "7.94",
    imgUrl:
      "https://cdn.arzdigital.com/uploads/assets/coins/icons/dogecoin.png",
    matchList: [
      {
        id: 1,
        timeframe: ["4h", "1w", "1d"],
        time: "7 hrs ago",
        isMached: true,
      },
      {
        id: 2,
        timeframe: ["4h", "1w", "1d"],
        time: "1 hrs ago",
        isMached: false,
      },
      {
        id: 3,
        timeframe: ["4h", "1w", "1d"],
        time: "7 hrs ago",
        isMached: true,
      },
      {
        id: 4,
        timeframe: ["4h", "1w", "1d"],
        time: "1 day ago",
        isMached: true,
      },
      {
        id: 5,
        timeframe: ["4h", "1w", "1d"],
        time: "1 day ago",
        isMached: false,
      },
    ],
  },
  {
    name: "usdc",
    price: "1,0000",
    pair: "usdt",
    percentage: "-0.02",
    imgUrl:
      "https://cdn.arzdigital.com/uploads/assets/coins/icons/usd-coin.png",
    matchList: [
      {
        id: 1,
        timeframe: ["4h", "1w", "1d"],
        time: "7 hrs ago",
        isMached: true,
      },
      {
        id: 2,
        timeframe: ["4h", "1w", "1d"],
        time: "1 hrs ago",
        isMached: false,
      },
      {
        id: 3,
        timeframe: ["4h", "1w", "1d"],
        time: "7 hrs ago",
        isMached: true,
      },
      {
        id: 4,
        timeframe: ["4h", "1w", "1d"],
        time: "1 day ago",
        isMached: true,
      },
      {
        id: 5,
        timeframe: ["4h", "1w", "1d"],
        time: "1 day ago",
        isMached: false,
      },
    ],
  },
]);

const isMobile = computed(() => {
  return window.innerWidth <= 500;
});

onMounted(() => {
  const parent = matchesContainer.value;
  parent.addEventListener("scroll", function () {
    showTitleBadge.value = parent.scrollLeft >= 220; // w-56;
  });
});
</script>

<template>
  <div class="md:p-10 h-screen w-full overflow-hidden">
    <div class="flex flex-row md:min-h-[576px] md:max-h-[576px]">
      <div
        class="hidden w-64 md:flex flex-col overflow-y-auto border-t border-b border-slate-200 px-2"
      >
        <div class="flex flex-col pb-2 border-b border-slate-200">
          <div class="flex flex-row justify-between items-center py-3">
            <h4 class="text-slate-800 font-medium text-sm">Strategy pack</h4>
            <div>
              <span class="text-slate-400 text-xs mr-2">4</span>
              <button class="text-slate-400 text-xs">⮟</button>
            </div>
          </div>

          <input
            class="placeholder:text-slate-400 text-slate-800 rounded-md border border-slate-200 py-2 px-4 mt-2"
            type="search"
            placeholder="Search"
          />

          <div class="my-2">
            <div>
              <div
                v-for="n in ['Binance', 'FTX', 'Coinbase', 'Kraken', 'KuCoin']"
                :key="n"
                class="flex justify-between items-center py-2"
              >
                <label
                  :for="n"
                  class="w-full flex flex-row justify-between items-center text-slate-800 capitalize"
                >
                  {{ n }}
                  <span class="text-slate-400 text-xs mr-2">1</span>
                </label>
                <input type="radio" :id="n" name="sample" :value="n" />
              </div>
            </div>
            <button
              class="text-blue-500 uppercase w-full rounded border border-blue-500 py-2 mt-2"
            >
              edit coin pack
            </button>
          </div>
        </div>
        <div class="flex flex-col pb-2 border-b border-slate-200">
          <div class="flex flex-row justify-between items-center py-3">
            <h4 class="text-slate-800 font-medium text-sm capitalize">
              exchange
            </h4>
            <div>
              <span class="text-slate-400 text-xs mr-2">12</span>
              <button class="text-slate-400 text-xs">⮟</button>
            </div>
          </div>

          <input
            class="placeholder:text-slate-400 text-slate-800 rounded-md border border-slate-200 py-2 px-4 mt-2"
            type="search"
            placeholder="Search"
          />

          <div class="my-2">
            <div>
              <div
                v-for="n in ['Binance', 'FTX', 'Coinbase', 'Kraken', 'KuCoin']"
                :key="n"
                class="flex justify-between items-center py-2"
              >
                <label
                  :for="n"
                  class="w-full flex flex-row justify-between items-center text-slate-800 capitalize"
                >
                  {{ n }}
                  <span class="text-slate-400 text-xs mr-2">1</span>
                </label>
                <input type="radio" :id="n" name="sample" :value="n" />
              </div>
            </div>
            <button
              class="text-blue-500 uppercase w-full rounded border border-blue-500 py-2 mt-2"
            >
              edit coin pack
            </button>
          </div>
        </div>
        <div class="flex flex-col pb-2 border-b border-slate-200">
          <div class="flex flex-row justify-between items-center py-3">
            <h4 class="text-slate-800 font-medium text-sm capitalize">
              pivot type
            </h4>
            <div>
              <span class="text-slate-400 text-xs mr-2"></span>
              <button class="text-slate-400 text-xs">⮟</button>
            </div>
          </div>

          <input
            class="placeholder:text-slate-400 text-slate-800 rounded-md border border-slate-200 py-2 px-4 mt-2"
            type="search"
            placeholder="Search"
          />

          <div class="my-2">
            <div>
              <div
                v-for="n in [
                  'Major',
                  'Maid major',
                  'minor',
                  'Kraken',
                  'super minor',
                ]"
                :key="n"
                class="flex justify-between items-center py-2"
              >
                <label
                  :for="n"
                  class="w-full flex flex-row justify-between items-center text-slate-800 capitalize"
                >
                  {{ n }}
                  <span class="text-slate-400 text-xs mr-2">1</span>
                </label>
                <input type="checkbox" :id="n" name="sample" :value="n" />
              </div>
            </div>
            <button
              class="text-blue-500 uppercase w-full rounded border border-blue-500 py-2 mt-2"
            >
              edit coin pack
            </button>
          </div>
        </div>
        <div class="flex flex-col pb-2 border-b border-slate-200">
          <div class="flex flex-row justify-between items-center py-3">
            <h4 class="text-slate-800 font-medium text-sm capitalize">
              cion pack
            </h4>
            <div>
              <span class="text-slate-400 text-xs mr-2">4</span>
              <button class="text-slate-400 text-xs">⮟</button>
            </div>
          </div>

          <input
            class="placeholder:text-slate-400 text-slate-800 rounded-md border border-slate-200 py-2 px-4 mt-2"
            type="search"
            placeholder="Search"
          />

          <div class="my-2">
            <div>
              <div
                v-for="n in ['metaverse top DEFI', 'top NFT', 'my coin pack']"
                :key="n"
                class="flex justify-between items-center py-2"
              >
                <label
                  :for="n"
                  class="w-full flex flex-row justify-between items-center text-slate-800 capitalize"
                >
                  {{ n }}
                  <span class="text-slate-400 text-xs mr-2">1</span>
                </label>
                <input type="radio" :id="n" name="sample" :value="n" />
              </div>
            </div>
            <button
              class="text-blue-500 uppercase w-full rounded border border-blue-500 py-2 mt-2"
            >
              edit coin pack
            </button>
          </div>
        </div>
        <div class="flex flex-col pb-2 border-b border-slate-200">
          <div class="flex flex-row justify-between items-center py-3">
            <h4 class="text-slate-800 font-medium text-sm capitalize">
              timeframe
            </h4>
            <div>
              <span class="text-slate-400 text-xs mr-2"></span>
              <button class="text-slate-400 text-xs">⮟</button>
            </div>
          </div>

          <div class="my-2">
            <div>
              <div
                v-for="n in ['5 min', '15 min', '30 min', '1H']"
                :key="n"
                class="flex justify-between items-center py-2"
              >
                <label
                  :for="n"
                  class="w-full flex flex-row justify-between items-center text-slate-800 capitalize"
                >
                  {{ n }}
                  <span class="text-slate-400 text-xs mr-2">1</span>
                </label>
                <input type="checkbox" :id="n" name="sample" :value="n" />
              </div>
            </div>
          </div>

          <div class="flex flex-row justify-between items-center py-3">
            <h4 class="text-slate-800 font-medium text-sm capitalize">pair</h4>
            <div>
              <span class="text-slate-400 text-xs mr-2"></span>
              <button class="text-slate-400 text-xs">⮟</button>
            </div>
          </div>

          <div class="my-2">
            <div>
              <div
                v-for="n in ['5 min', '15 min', '30 min', '1H']"
                :key="n"
                class="flex justify-between items-center py-2"
              >
                <label
                  :for="n"
                  class="w-full flex flex-row justify-between items-center text-slate-800 capitalize"
                >
                  {{ n }}
                  <span class="text-slate-400 text-xs mr-2">1</span>
                </label>
                <input type="checkbox" :id="n" name="sample" :value="n" />
              </div>
            </div>
          </div>

          <div class="flex flex-row justify-between items-center py-3">
            <h4 class="text-slate-800 font-medium text-sm capitalize">
              volume
            </h4>
            <div>
              <span class="text-slate-400 text-xs mr-2"></span>
              <button class="text-slate-400 text-xs">⮟</button>
            </div>
          </div>

          <div class="my-2 flex flex-col">
            <input
              class="placeholder:text-center placeholder:text-slate-400 border border-slate-200 rounded px-4 py-2"
              placeholder="from"
            />
            <input
              class="placeholder:text-center placeholder:text-slate-400 border border-slate-200 rounded px-4 py-2 mt-2.5"
              placeholder="to"
            />
            <button
              class="text-white bg-blue-500 capitalize rounded px-4 py-2 mt-3"
            >
              apply
            </button>
          </div>
        </div>
      </div>
      <div class="w-full relative overflow-hidden">
        <div
          v-if="isMobile"
          class="absolute h-full w-10 bg-white transition-all duration-200 shadow-lg"
          :class="showTitleBadge ? 'left-0 opacity-100' : '-left-100 opacity-0'"
        >
          <div
            class="h-20 md:h-24 font-medium writing-v-lr w-full grid place-items-center capitalize border-slate-200 border-r border-b"
          >
            <span>coin</span>
          </div>
          <div
            v-for="coin in coinList"
            :key="coin.name"
            class="h-20 md:h-24 w-full grid place-items-center border-b border-slate-200 border-r"
          >
            <img
              class="w-6 h-6"
              :title="coin.name"
              :alt="coin.name"
              :src="coin.imgUrl"
            />
            <span
              class="writing-v-lr uppercase font-medium text-xs"
              v-text="coin.name"
            ></span>
          </div>
        </div>
        <div
          class="flex-1 flex flex-col overflow-x-auto"
          ref="matchesContainer"
        >
          <!-- strategy row -->
          <div class="flex flex-row">
            <!-- exchange info -->
            <div
              class="h-20 md:h-24 w-56 md:w-64 flex-none flex flex-row justify-between items-center px-6 border-l border-t border-b border-slate-200"
            >
              <h4 class="uppercase font-bold text-amber-500">binance</h4>
              <button
                class="rounded border border-slate-200 w-10 h-10 text-xl text-slate-800"
              >
                &#8635;
              </button>
            </div>
            <!-- strategy item -->
            <div
              v-for="strategy in strategyList"
              :key="strategy.name"
              class="h-20 md:h-24 w-56 md:w-64 flex flex-col justify-between px-4 py-3 flex-none border-l border-t border-b border-slate-200"
            >
              <div class="flex flex-row justify-between items-start">
                <h4
                  class="text-sm font-medium text-slate-800"
                  v-text="strategy.name"
                ></h4>
                <button class="text-slate-400 text-xs">X</button>
              </div>
              <div class="flex flex-row justify-between items-center">
                <div class="flex items-center">
                  <h4 class="text-xs text-slate-400 mr-2">Price Action</h4>
                  <div
                    class="text-white text-[10px] rounded-xl px-2 py-0.5"
                    :class="{
                      'bg-teal-500': strategy.positionBuy,
                      'bg-rose-500': !strategy.positionBuy,
                    }"
                  >
                    <span v-if="strategy.positionBuy">Buy</span>
                    <span v-else>Sell</span>
                  </div>
                </div>
                <button class="text-slate-400 text-xs">&#11167;</button>
              </div>
            </div>
          </div>
          <!-- match rows -->
          <div class="flex flex-col">
            <!-- row -->
            <div
              v-for="coin in coinList"
              :key="coin.name"
              class="flex flex-row"
            >
              <!-- coin inof -->
              <div
                class="w-56 md:w-64 h-20 md:h-24 flex-none flex flex-row justify-between items-center px-3 md:px-6 border-b border-l border-slate-200"
              >
                <img
                  class="w-10 h-10 mr-2"
                  :title="coin.name"
                  :alt="coin.name"
                  :src="coin.imgUrl"
                />
                <div class="flex flex-col flex-1">
                  <div class="flex flex-row items-center">
                    <h4
                      class="font-medium text-base text-slate-800 uppercase"
                      v-text="coin.name"
                    ></h4>
                    <h6
                      class="text-xs ml-2"
                      :class="{
                        'text-teal-500': coin.percentage > 0,
                        'text-rose-500': coin.percentage <= 0,
                      }"
                    >
                      {{ coin.percentage }}%
                    </h6>
                  </div>
                  <div class="flex flex-row items-center">
                    <span class="text-slate-400 text-xs">24,000</span>
                    <span class="uppercase text-slate-400 text-xs ml-2"
                      >usdt</span
                    >
                  </div>
                </div>
                <div>
                  <div
                    class="text-slate-400 text-xs w-10 h-10 grid place-items-center"
                  >
                    <span>&#11166;</span>
                  </div>
                </div>
              </div>
              <!-- match item -->
              <div
                v-for="match in coin.matchList"
                :key="match.id"
                class="flex flex-col justify-between px-4 py-5 flex-none w-56 md:w-64 h-20 md:h-24 border-b border-l border-slate-200"
              >
                <div class="flex flex-row justify-between items-center">
                  <div
                    class="flex items-center"
                    :class="{
                      'text-teal-500': match.isMached,
                      'text-rose-500': !match.isMached,
                    }"
                  >
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      class="w-4 h-4"
                      viewBox="0 0 24 24"
                      fill="none"
                      stroke="currentColor"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    >
                      <path d="M18 8A6 6 0 0 0 6 8c0 7-3 9-3 9h18s-3-2-3-9" />
                      <path d="M13.73 21a2 2 0 0 1-3.46 0" />
                    </svg>

                    <span class="font-medium text-sm ml-2">Match</span>
                  </div>
                  <div
                    class="rounded-lg bg-slate-100 px-2.5 py-0.5 flex flex-row text-[10px] text-slate-400"
                  >
                    <div
                      v-for="timeframe in match.timeframe.splice(0, 2)"
                      :key="timeframe"
                    >
                      <span v-text="timeframe"></span>
                      <span class="mx-0.5">|</span>
                    </div>
                    ...
                  </div>
                </div>
                <div class="flex flex-row justify-between">
                  <span class="text-[10px] text-slate-800"
                    >Minor Pivot Type</span
                  >
                  <div class="flex flex-row items-center">
                    <span
                      class="text-[10px] text-slate-400 mr-1.5"
                      v-text="match.time"
                    ></span>
                    <svg
                      class="fill-teal-500"
                      width="12"
                      height="6.009"
                      viewBox="0 0 12 6.009"
                    >
                      <g transform="translate(-33.99 -23.907)">
                        <path
                          d="M41.382,24.085a.6.6,0,1,1,.851.846q-2.428,2.4-4.859,4.8a.606.606,0,0,1-.862,0q-1.154-1.192-2.305-2.387a.641.641,0,0,1-.216-.435.6.6,0,0,1,1.045-.438q.96.991,1.918,1.985Z"
                          transform="translate(0 0)"
                        />
                        <path
                          d="M154.622,24.458a.6.6,0,0,1,.612.993q-2.416,2.391-4.834,4.78a.6.6,0,0,1-.838.026c-.211-.212-.416-.43-.622-.647a.6.6,0,0,1,.65-.966,1.067,1.067,0,0,1,.39.314l4.167-4.12C154.3,24.7,154.42,24.52,154.622,24.458Z"
                          transform="translate(-109.416 -0.498)"
                        />
                      </g>
                    </svg>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.writing-v-lr {
  writing-mode: vertical-lr;
}
</style>
