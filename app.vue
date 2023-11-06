<template>
  <main class="flex pb-20">
    <img
      class="max-h-40"
      src="https://static.thenounproject.com/png/331759-200.png"
      alt="{"
    />

    <form
      @submit.prevent="handleSubmit"
      class="md:text-2xl text-sm -ml-10 pt-6 space-y-7"
    >
      <div>
        <input
          type="number"
          v-model="store.a"
          class="w-20 text-end"
          max="9999"
          required
        />
        x +
        <input
          type="number"
          v-model="store.b"
          class="w-20 text-end"
          max="9999"
          required
        />
        y =
        <input
          type="number"
          v-model="store.c"
          class="w-20"
          max="9999"
          required
        />
      </div>
      <div>
        <input
          type="number"
          v-model="store.a1"
          class="w-20 text-end"
          max="9999"
          required
        />
        x +
        <input
          type="number"
          v-model="store.b1"
          class="w-20 text-end"
          max="9999"
          required
        />
        y =
        <input
          type="number"
          v-model="store.c1"
          class="w-20"
          max="9999"
          required
        />
      </div>
      <button class="h-10 px-10 active:border-blue-600 active:bg-white active:text-blue-600 border-2 -ml-10 bg-blue-600 rounded-full text-white" type="submit">Send</button>

      <div v-if="store.isSubmit" class="-ml-10 space-y-7">
        <p class="flex items-center gap-2 w-full">1<hr class="w-full border-2 border-red-600" /></p>
      <!-- 1 -->
      <div class="flex flex-wrap items-center gap-10">
        <div class="flex items-center gap-10 w-[350px]">
          <div class="flex flex-col items-center max-w-fit">
            <p class="border-b">{{ store.a }}</p>
            <p>{{ store.a1 }}</p>
          </div>
          <div class="flex items-center">
            &lt= <span class="rotate-180 mt-2 inline-block">&lt</span>
          </div>
          <div class="flex flex-col items-center max-w-fit">
            <p class="border-b">{{ store.b }}</p>
            <p>{{ store.b1 }}</p>
          </div>
        </div>
        <div class="border-b-2 border-black">
          {{ store.a }} * {{ store.b1 }} - {{ store.a1 }} * {{ store.b }} =
          {{ store.res1 }}
        </div>
      </div>

      <p class="flex items-center gap-2 w-full">2<hr class="w-full border-2 border-red-600" /></p>

      <!-- 2 -->
      <div class="flex flex-wrap items-center gap-10">
        <div class="flex items-center gap-10 w-[350px]">
          <div class="flex flex-col items-center max-w-fit">
            <p class="border-b">{{ store.c }}</p>
            <p>{{ store.c1 }}</p>
          </div>
          <div class="flex items-center">
            &lt= <span class="rotate-180 mt-2 inline-block">&lt</span>
          </div>
          <div class="flex flex-col items-center max-w-fit">
            <p class="border-b">{{ store.b }}</p>
            <p>{{ store.b1 }}</p>
          </div>
        </div>
        <div class="border-b-2 border-black">
          {{ store.c }} * {{ store.b1 }} - {{ store.c1 }} * {{ store.b }} =
          {{ store.res2 }}
        </div>
      </div>

      <p class="flex items-center gap-2 w-full">3<hr class="w-full border-2 border-red-600" /></p>
      <!-- 3 -->
      <div class="flex flex-wrap items-center gap-10">
        <div class="flex items-center gap-10 w-[350px]">
          <div class="flex flex-col items-center max-w-fit">
            <p class="border-b">{{ store.a }}</p>
            <p>{{ store.a1 }}</p>
          </div>
          <div class="flex items-center">
            &lt= <span class="rotate-180 mt-2 inline-block">&lt</span>
          </div>
          <div class="flex flex-col items-center max-w-fit">
            <p class="border-b">{{ store.c }}</p>
            <p>{{ store.c1 }}</p>
          </div>
        </div>
        <div class="border-b-2 border-black">
          {{ store.a }} * {{ store.c1 }} - {{ store.a1 }} * {{ store.c }} =
          {{ store.res3 }}
        </div>
        <div class="space-y-2 w-full">
          <h1 class="font-bold text-red-600">Result:</h1>
          <div class="flex items-center w-full gap-2">
            <p class="whitespace-nowrap">x =</p>
            <div class="flex flex-col items-center max-w-fit">
              <p class="border-b">{{ store.res2 }}</p>
              <p>{{ store.res1 }}</p>
            </div>
            =>
            <p class="border-b-2 border-black">{{ store.x }}</p>
          </div>
          <div class="flex items-center w-full gap-2">
            <p class="whitespace-nowrap">y =</p>
            <div class="flex flex-col items-center max-w-fit">
              <p class="border-b">{{ store.res3 }}</p>
              <p>{{ store.res1 }}</p>
            </div>
            =>
            <p class="border-b-2 border-black">{{ store.y }}</p>
          </div>
        </div>
      </div>
      </div>
    </form>
  </main>
</template>

<script setup>
const store = reactive({
  a: "",
  b: "",
  c: "",
  a1: "",
  b1: "",
  c1: "",
  res1: "",
  res2: "",
  res3: "",
  isSubmit: false,
  x: "",
  y: "",
});

function handleSubmit() {
  store.res1 = store.a * store.b1 - store.a1 * store.b;
  store.res2 = store.c * store.b1 - store.c1 * store.b;
  store.res3 = store.a * store.c1 - store.a1 * store.c;
  store.x = store.res2 / store.res1;
  store.y = store.res3 / store.res1;
  store.isSubmit = true;
}

onMounted(()=> {
  const input = document.querySelectorAll("input")
  for (let i of input){
    i.addEventListener("input", () => {
      store.isSubmit = false;
    })
  }
})
</script>
