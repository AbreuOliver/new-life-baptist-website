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
    { radius: 1200, animClass: "animate-[spin_8s_linear_infinite]" },
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
    "pointer-events-none my-auto text-xs font-normal leading-none max-w-full flex-initial bg-white primary-serif";
  const titleClass =
    "pointer-events-none text-4xl md:text-5xl font-black tracking-tight text-zinc-900 w-9/12 mx-auto";
  const subtitleClass =
    "pointer-events-none mt-4 text-zinc-600 text-xl leading-7 w-9/12 md:w-6/12 mx-auto primary-serif tracking-wider";
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
</script>

<section class={sectionClass} aria-labelledby="orbit-hero-title">
  <div class={`${ringsShellClass} mb-20 md:mb-0`} aria-hidden="true">
    <div class={ringsShellClass} aria-hidden="true">
      {#each spinners as { radius, animClass }}
        <Spinner {radius} {animClass} />
      {/each}
    </div>

    <div class={fgShellClass}>
      <div class={innerStackClass}>
        <div class={badgeWrapClass}>
          <div class={badgeTextClass}>2 Corinthians 5:17</div>
        </div>

        <h1 id="orbit-hero-title" class={titleClass}>{title}</h1>
        <p class={subtitleClass} style="margin-bottom: 3rem;">{subtitle}</p>

        <!-- <div
          class="flex flex-col md:flex-row gap-4 md:gap-8 justify-center mb-8 animate-fade-in text-zinc-800/60 primary-serif"
        >
          <div class="flex items-center justify-center gap-2">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
              class="lucide lucide-clock h-5 w-5"
              ><circle cx="12" cy="12" r="10"></circle><polyline
                points="12 6 12 12 16 14"
              ></polyline></svg
            ><span class="font-medium">Sundays: 9:00 AM &amp; 11:00 AM</span>
          </div>
          <div class="flex items-center justify-center gap-2">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
              class="lucide lucide-map-pin h-5 w-5"
              ><path
                d="M20 10c0 4.993-5.539 10.193-7.399 11.799a1 1 0 0 1-1.202 0C9.539 20.193 4 14.993 4 10a8 8 0 0 1 16 0"
              ></path><circle cx="12" cy="10" r="3"></circle></svg
            ><span class="font-medium"
              >5501 Lloyd Ave., White Marsh, MD 21162</span
            >
          </div>
        </div> -->

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

<!-- <section class={sectionClass} aria-labelledby="orbit-hero-title">
  <div
    class="absolute inset-0 z-0 object-cover bg-center"
    style="background-image: url('https://ik.imagekit.io/bip1v395ybp/New%20Life%20Baptist%20Church/pastor_2Eo0Wdfqm.jpg?updatedAt=1762366795990');"
  ></div>

  <div
    class="absolute inset-0 z-0"
    style="background-color: rgba(0, 0, 0, 0.4);"
  ></div>

  <div class={`${ringsShellClass} mb-20 md:mb-0`} aria-hidden="true">
    <div class={`${ringsShellClass} z-10`} aria-hidden="true">
      {#each spinners as { radius, animClass }}
        <Spinner {radius} {animClass} />
      {/each}
    </div>

    <div class={fgShellClass}>
      <div class={innerStackClass}>
        <div class={badgeWrapClass}>
          <div class={badgeTextClass}>2 Corinthians 5:17</div>
        </div>

        <h1 id="orbit-hero-title" class={`${titleClass} z-20`}>{title}</h1>
        <p class={subtitleClass} style="margin-bottom: 3rem;">{subtitle}</p>

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
</section> -->
