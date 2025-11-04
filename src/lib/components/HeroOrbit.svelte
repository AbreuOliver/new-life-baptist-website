<!-- <script lang="ts">
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

  <div
    class="pointer-events-none absolute inset-0 grid place-items-center mb-20 md:mb-0"
    aria-hidden="true"
  >

    <div
      class="pointer-events-none absolute inset-0 grid place-items-center"
      aria-hidden="true"
    >
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
</section> -->

<script lang="ts">
  import Spinner from "./Spinner.svelte";

  export let title = "The home for developer communities";
  export let subtitle =
    "Ask questions, share ideas, and build connections with each other — all right next to your code.";
  export let cta = { label: "Enable discussions →", href: "#" };
  export let secondary = { label: "Watch video", href: "#" };

  // Spinner config (DRY)
  const spinners = [
    { radius: 400, animClass: "animate-[spin_5s_linear_infinite]" },
    { radius: 550, animClass: "animate-[spin_7s_linear_infinite_reverse]" },
    { radius: 700, animClass: "animate-[spin_9s_linear_infinite]" },
    { radius: 850, animClass: "animate-[spin_11s_linear_infinite_reverse]" },
    { radius: 1000, animClass: "animate-[spin_11s_linear_infinite_reverse]" },
  ];

  // Reused classes (no visual change)
  const sectionClass = "relative isolate overflow-hidden w-screen min-h-[85vh]";
  const ringsShellClass =
    "pointer-events-none absolute inset-0 grid place-items-center";
  const fgShellClass =
    "pointer-events-auto flex flex-col justify-center items-center z-5 mx-auto w-full min-h-[85vh] h-full";

  const innerStackClass =
    "mx-auto max-w-2xl space-y-8 text-center w-12/12 absolute bottom-0 md:relative";
  const badgeWrapClass =
    "flex justify-center items-center m-1 font-medium py-2 px-4 rounded-full text-zinc-700 bg-white border border-zinc-300 w-fit mx-auto shadow-sm";
  const badgeTextClass =
    "pointer-events-none my-auto text-xs font-normal leading-none max-w-full flex-initial bg-white";
  const titleClass =
    "pointer-events-none text-4xl md:text-5xl font-black tracking-tight text-zinc-900 w-9/12 mx-auto";
  const subtitleClass =
    "pointer-events-none mt-4 text-zinc-600 text-lg leading-7 special-serif w-9/12 mx-auto";
  const ctaRowClass = "mt-8 flex flex-col items-center justify-center gap-4";

  const baseBtn =
    "inline-flex items-center justify-center rounded-md px-6 py-3 text-base font-normal " +
    "transition-transform duration-150 ease-out cursor-pointer " +
    "focus:outline-none focus-visible:ring-2 md:w-60 w-11/12 mx-auto " +
    "hover:shadow-sm md:hover:shadow-md hover:-translate-y-[1px] " +
    "active:translate-y-0 motion-reduce:transition-none";

  const primaryBtnClass =
    baseBtn +
    " bg-zinc-900 text-white hover:bg-zinc-800 focus-visible:ring-zinc-400";

  const secondaryBtnClass =
    baseBtn +
    " border border-zinc-300 bg-white text-zinc-900 hover:bg-zinc-100 " +
    "focus-visible:ring-zinc-300";

  // const primaryBtnClass =
  //   "inline-flex items-center justify-center rounded-md bg-zinc-900 px-6 py-3 text-base " +
  //   "font-normal text-white hover:bg-zinc-800 focus:outline-none focus-visible:ring-2 " +
  //   "focus-visible:ring-zinc-400 md:w-60 w-11/12 mx-auto";
  // const secondaryBtnClass =
  //   "inline-flex items-center justify-center rounded-md border border-zinc-300 bg-white px-6 py-3 text-base " +
  //   "font-normal text-zinc-900 hover:bg-zinc-50 focus:outline-none focus-visible:ring-2 " +
  //   "focus-visible:ring-zinc-300 md:w-60 w-11/12 mx-auto";
</script>

<section class={sectionClass} aria-labelledby="orbit-hero-title">
  <!-- Background concentric guide rings -->
  <div class={`${ringsShellClass} mb-20 md:mb-0`} aria-hidden="true">
    <div class={ringsShellClass} aria-hidden="true">
      {#each spinners as { radius, animClass }}
        <Spinner {radius} {animClass} />
      {/each}
    </div>

    <!-- Foreground content -->
    <div class={fgShellClass}>
      <div class={innerStackClass}>
        <div class={badgeWrapClass}>
          <div class={badgeTextClass}>2 Corinthians 5:17</div>
        </div>

        <h1 id="orbit-hero-title" class={titleClass}>{title}</h1>
        <p class={subtitleClass}>{subtitle}</p>

        <div class={ctaRowClass}>
          <a href={cta.href} class={primaryBtnClass}>{cta.label}</a>
          {#if secondary?.href}
            <a href={secondary.href} class={secondaryBtnClass}>
              {secondary.label}
            </a>
          {/if}
        </div>
      </div>
    </div>
  </div>
</section>
