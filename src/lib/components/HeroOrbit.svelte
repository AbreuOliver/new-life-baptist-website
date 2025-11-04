<script lang="ts">
  import Spinner from "./Spinner.svelte";
  import SpinningRing from "./SpinningRing.svelte";
  export let title = "The home for developer communities";
  export let subtitle =
    "Ask questions, share ideas, and build connections with each other — all right next to your code.";
  export let cta = { label: "Enable discussions →", href: "#" };
  export let secondary = { label: "Watch video", href: "#" };
</script>

<section
  class="relative isolate overflow-hidden w-screen min-h-[85vh]"
  aria-labelledby="orbit-hero-title"
>
  <!-- Background concentric guide rings -->
  <div
    class="pointer-events-none absolute inset-0 grid place-items-center"
    aria-hidden="true"
  >
    <!-- <svg
      viewBox="0 0 1026 1026"
      fill="none"
      aria-hidden="true"
      class="absolute inset-0 h-full w-full animate-[spin_5s_linear_infinite]"
      ><path
        d="M1025 513c0 282.77-229.23 512-512 512S1 795.77 1 513 230.23 1 513 1s512 229.23 512 512Z"
        stroke="#D4D4D4"
        stroke-opacity="0.7"
      ></path><path
        d="M513 1025C230.23 1025 1 795.77 1 513"
        stroke="url(#_S_3_-gradient-1)"
        stroke-linecap="round"
      ></path><defs
        ><linearGradient
          id="_S_3_-gradient-1"
          x1="1"
          y1="513"
          x2="1"
          y2="1025"
          gradientUnits="userSpaceOnUse"
          >`<stop stop-color="var(--color-cta-from)"></stop><stop
            offset="1"
            stop-color="var(--color-brand-500)"
            stop-opacity="0"
          ></stop>`</linearGradient
        ></defs
      ></svg
    > -->
    <!-- <svg
      viewBox="0 0 1026 1026"
      fill="none"
      aria-hidden="true"
      class="absolute inset-0 h-full w-full animate-[spin_7s_linear_infinite_reverse]"
      ><path
        d="M913 513c0 220.914-179.086 400-400 400S113 733.914 113 513s179.086-400 400-400 400 179.086 400 400Z"
        stroke="#D4D4D4"
        stroke-opacity="0.7"
      ></path><path
        d="M913 513c0 220.914-179.086 400-400 400"
        stroke="url(#_S_3_-gradient-2)"
        stroke-linecap="round"
      ></path><defs
        ><linearGradient
          id="_S_3_-gradient-2"
          x1="913"
          y1="513"
          x2="913"
          y2="913"
          gradientUnits="userSpaceOnUse"
          >`<stop stop-color="var(--color-brand-500)"></stop><stop
            offset="1"
            stop-color="var(--color-cta-from)"
            stop-opacity="0"
          ></stop>`</linearGradient
        ></defs
      ></svg
    > -->
    <div
      class="pointer-events-none absolute inset-0 grid place-items-center"
      aria-hidden="true"
    >
      <!-- <SpinningRing
        radius={400}
        animClass="animate-[spin_8s_linear_infinite_reverse]"
        fromColor="#000"
        toColor="#333"
        tail={0.1}
        headHold={2}
      />
      <SpinningRing
        radius={550}
        animClass="animate-[spin_8s_linear_infinite]"
        fromColor="#ECAAFB"
        toColor="#05BBF8"
        tail={0.9}
        headHold={0.1}
      />
      <SpinningRing
        radius={400 + 150 + 150}
        animClass="animate-[spin_10s_linear_infinite_reverse]"
        tail={0.9}
        headHold={0.1}
      />
      <SpinningRing
        radius={700 + 150}
        animClass="animate-[spin_12s_linear_infinite]"
        tail={0.9}
        headHold={0.1}
      />
      <SpinningRing
        radius={700 + 150 + 150}
        animClass="animate-[spin_14s_linear_infinite_reverse]"
        tail={0.9}
        headHold={0.1}
      /> -->
      <Spinner radius={400} animClass="animate-[spin_5s_linear_infinite]" />
      <Spinner
        radius={550}
        animClass="animate-[spin_7s_linear_infinite_reverse]"
      />
      <Spinner radius={700} animClass="animate-[spin_9s_linear_infinite]" />
      <Spinner
        radius={850}
        animClass="animate-[spin_11s_linear_infinite_reverse]"
      />
      <Spinner
        radius={1000}
        animClass="animate-[spin_11s_linear_infinite_reverse]"
      />
    </div>

    <!-- Foreground content -->
    <div
      class="flex flex-col justify-center items-center z-5 mx-auto w-full min-h-[85vh] h-full"
    >
      <div
        class="mx-auto max-w-2xl space-y-8 text-center w-12/12 absolute bottom-0 md:relative"
      >
        <div
          class="flex justify-center items-center m-1 font-medium py-2 px-4 rounded-full text-zinc-700 bg-white border border-zinc-300 w-fit mx-auto shadow-sm"
        >
          <div
            class="my-auto text-xs font-normal leading-none max-w-full flex-initial bg-white"
          >
            2 Corinthians 5:17
          </div>
        </div>

        <h1
          id="orbit-hero-title"
          class="text-4xl md:text-5xl font-black tracking-tight text-zinc-900 w-9/12 mx-auto"
        >
          {title}
        </h1>
        <p
          class="mt-4 text-zinc-600 text-lg leading-7 special-serif w-9/12 mx-auto"
        >
          {subtitle}
        </p>

        <div class="mt-8 flex flex-col items-center justify-center gap-4">
          <a
            href={cta.href}
            class="inline-flex items-center justify-center rounded-md bg-zinc-900 px-6 py-3 text-base font-normal text-white hover:bg-zinc-800 focus:outline-none focus-visible:ring-2 focus-visible:ring-zinc-400 md:w-60 w-11/12 mx-auto"
          >
            {cta.label}
          </a>
          {#if secondary?.href}
            <a
              href={secondary.href}
              class="inline-flex items-center justify-center rounded-md border border-zinc-300 bg-white px-6 py-3 text-base font-normal text-zinc-900 hover:bg-zinc-50 focus:outline-none focus-visible:ring-2 focus-visible:ring-zinc-300 md:w-60 w-11/12 mx-auto"
            >
              {secondary.label}
            </a>
          {/if}
        </div>
      </div>
    </div>
  </div>
</section>
