<script lang="ts">
  import { browser } from "$app/environment";
  import { onMount, tick, createEventDispatcher } from "svelte";

  // ---------- API (props) ----------
  export let isBannerVisible: boolean = true; // controlled visibility (still works as before)
  export let href: string | null = "/about#childrens-ministry";
  export let title: string = "Friendsgiving Lunch";
  export let date: string | Date | null = "Nov 23";
  export let subtitle: string | null = "You're invited!";
  export let dismissible: boolean = true;
  export let id: string | null = null; // needed if you want per-user dismiss persistence
  export let persistDismiss: boolean = false; // if true and id is provided, dismissal is saved
  export let ariaLabel: string = "Site announcement";
  export let variant: "amber" | "blue" | "green" | "neutral" = "amber";
  export let ariaLive: "polite" | "assertive" | "off" = "polite";

  // ---------- internal ----------
  const dispatch = createEventDispatcher<{ close: void }>();

  let root: HTMLElement | null = null;
  let ro: ResizeObserver | null = null;
  let mounted = false;

  const variantClasses: Record<typeof variant, string> = {
    amber: "bg-amber-300 ring-amber-800/10 text-zinc-900",
    blue: "bg-blue-300 ring-blue-800/10 text-zinc-900",
    green: "bg-green-300 ring-green-800/10 text-zinc-900",
    neutral: "bg-neutral-200 ring-neutral-500/10 text-zinc-900",
  };

  function setOffset(px: number) {
    if (!browser) return; // SSR guard
    document.documentElement.style.setProperty("--banner-h", `${px}px`);
  }

  async function applyOffset() {
    if (!mounted) return;
    await tick();
    if (isBannerVisible && root) {
      setOffset(root.offsetHeight || 0);
    } else {
      setOffset(0);
    }
  }

  function formatDate(d: string | Date | null): string | null {
    if (!d) return null;
    try {
      if (typeof d === "string") return d; // assume preformatted if string
      // format Date object
      return new Intl.DateTimeFormat(undefined, {
        month: "short",
        day: "numeric",
      }).format(d);
    } catch {
      return typeof d === "string" ? d : null;
    }
  }

  function closeBanner() {
    isBannerVisible = false;
    if (persistDismiss && id && browser) {
      try {
        localStorage.setItem(`banner:${id}:dismissed`, "1");
      } catch {}
    }
    dispatch("close");
    applyOffset();
  }

  onMount(() => {
    mounted = true;

    // read persisted dismissal
    if (persistDismiss && id && browser) {
      try {
        const dismissed =
          localStorage.getItem(`banner:${id}:dismissed`) === "1";
        if (dismissed) isBannerVisible = false;
      } catch {}
    }

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
    role="region"
    aria-label={ariaLabel}
    aria-live={ariaLive}
    class={`sticky top-0 z-[60] w-full shadow-sm ring-1 primary-serif text-xl ${variantClasses[variant]}`}
  >
    <div
      aria-hidden="true"
      class="pointer-events-none absolute inset-0 -z-10"
    ></div>

    <div
      class="flex items-center mx-auto w-full max-w-[95vw] md:max-w-[850px] px-4 py-3 md:h-14 md:py-0"
    >
      <div class="flex items-center gap-3 w-full">
        {#if href}
          <a
            {href}
            class="group flex flex-1 items-start justify-center gap-2 md:gap-3 mr-auto leading-6"
          >
            <slot name="icon">
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
            </slot>

            <span class="group-hover:underline">
              <slot>
                <span class="font-semibold">{title}</span>
                {#if date}
                  <span aria-hidden="true" class="mx-1">·</span>
                  <span>{formatDate(date)}</span>
                {/if}
                {#if subtitle}
                  <span aria-hidden="true" class="mx-1">·</span>
                  <span>{subtitle}</span>
                {/if}
              </slot>
            </span>
          </a>
        {:else}
          <div
            class="group flex flex-1 items-start justify-center gap-2 md:gap-3 mr-auto leading-6"
          >
            <slot name="icon">
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
            </slot>
            <span>
              <slot>
                <span class="font-semibold">{title}</span>
                {#if date}
                  <span aria-hidden="true" class="mx-1">·</span>
                  <span>{formatDate(date)}</span>
                {/if}
                {#if subtitle}
                  <span aria-hidden="true" class="mx-1">·</span>
                  <span>{subtitle}</span>
                {/if}
              </slot>
            </span>
          </div>
        {/if}

        <slot name="actions" />

        {#if dismissible}
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
        {/if}
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
