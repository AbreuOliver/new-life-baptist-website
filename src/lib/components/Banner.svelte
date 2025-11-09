<script lang="ts">
  import { browser } from "$app/environment";

  import { onMount, onDestroy, tick } from "svelte";

  export let isBannerVisible = true;

  let root: HTMLElement | null = null;
  let ro: ResizeObserver | null = null;
  let mounted = false;

  function setOffset(px: number) {
    if (!browser) return; // SSR guard
    document.documentElement.style.setProperty("--banner-h", `${px}px`);
  }

  async function applyOffset() {
    if (!mounted) return; // don’t run during SSR or before mount
    await tick();
    if (isBannerVisible && root) {
      setOffset(root.offsetHeight || 0);
    } else {
      setOffset(0);
    }
  }

  function closeBanner() {
    isBannerVisible = false;
    applyOffset();
  }

  onMount(() => {
    mounted = true;

    // initial measure
    applyOffset();

    // observe size changes
    if ("ResizeObserver" in window && root) {
      ro = new ResizeObserver(() => applyOffset());
      ro.observe(root);
    }

    return () => {
      if (ro) ro.disconnect();
      setOffset(0);
      mounted = false;
    };
  });

  // Re-run when visibility changes, but only after mount
  $: if (mounted) applyOffset();
</script>

{#if isBannerVisible}
  <div
    bind:this={root}
    class="sticky top-0 z-50 w-full bg-amber-300 shadow-sm ring-1 ring-amber-800/10 text-zinc-900 primary-serif text-xl"
  >
    <div
      aria-hidden="true"
      class="pointer-events-none absolute inset-0 -z-10
             before:content-[''] before:absolute before:inset-y-0 before:w-[45%]
             before:-skew-x-12 before:bg-gradient-to-r before:from-white/0 before:via-white/35 before:to-white/0
             before:translate-x-[-120%] before:animate-[shine_2500ms_linear_infinite]"
    ></div>

    <div
      class="flex items-center mx-auto w-full max-w-[95vw] md:max-w-[850px] px-4 md:h-14 py-3 md:py-0"
    >
      <div class="flex items-center gap-3 w-full">
        <a
          href="/about#childrens-ministry"
          class="group flex flex-1 items-center justify-center gap-2 md:gap-3 mr-auto leading-6"
        >
          <!-- decorative icon -->
          <svg
            class="shrink-0 w-5 h-5"
            aria-hidden="true"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
          >
            <path
              fill="none"
              stroke="currentColor"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M4 7a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2v12a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2zm12-4v4M8 3v4m-4 4h16M8 14v4m4-4v4m4-4v4"
            />
          </svg>

          <!-- text (underline only on hover) -->
          <span class="group-hover:underline">
            <span class="font-semibold">Friendsgiving Lunch</span>
            <span aria-hidden="true" class="mx-1">·</span>
            <span class="whitespace-nowrap">Nov 23</span>
            <span aria-hidden="true" class="mx-1 hidden sm:inline">·</span>
            <span class="hidden sm:inline">You're invited!</span>
          </span>
        </a>

        <button
          on:click={closeBanner}
          type="button"
          class="shrink-0 inline-flex justify-center items-center w-8 h-8 text-sm rounded-full text-neutral-700 hover:bg-red-600 hover:text-white transition"
          aria-label="Close banner"
        >
          <svg
            class="w-3 h-3"
            aria-hidden="true"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 14 14"
          >
            <path
              stroke="currentColor"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="m1 1 6 6m0 0 6 6M7 7l6-6M7 7l-6 6"
            />
          </svg>
        </button>
      </div>
    </div>
  </div>
{/if}

<style>
  @keyframes shine {
    0% {
      transform: translateX(-120%);
    }
    70% {
      transform: translateX(120%);
    }
    100% {
      transform: translateX(120%);
    }
  }
</style>
