<script lang="ts">
  /**
   * PaperPage — analog “scanned paper” aesthetic.
   *
   * Props:
   * - tone: 'green' | 'cream' | 'gray' — base paper color
   * - grid: number (px) — spacing for ledger lines
   * - holes: number — number of punch holes on the left
   * - showHoles: boolean — toggle punched holes
   * - class: string — extra classes for the outer wrapper
   */

  export let tone: "green" | "cream" | "gray" = "green";
  export let grid = 20;
  export let holes = 6;
  export let showHoles = true;
  export let className: string = "";
</script>

<section
  class={`relative isolate overflow-hidden rounded-lg ring-1 ring-black/10 shadow-sm ${className}`}
  style="
    --grid: {grid}px;
    --paper-green: 140 30% 78%;
    --paper-cream: 48 45% 90%;
    --paper-gray : 210 10% 92%;
  "
>
  {#if tone === "green"}
    <div class="absolute inset-0 -z-30 bg-[hsl(var(--paper-green))]"></div>
  {:else if tone === "cream"}
    <div class="absolute inset-0 -z-30 bg-[hsl(var(--paper-cream))]"></div>
  {:else}
    <div class="absolute inset-0 -z-30 bg-[hsl(var(--paper-gray))]"></div>
  {/if}

  <!-- 1) Textured paper grain (live SVG turbulence; no external image) -->
  <svg
    class="pointer-events-none absolute inset-0 -z-20 opacity-40 mix-blend-multiply"
    aria-hidden="true"
    viewBox="0 0 100 100"
    preserveAspectRatio="none"
  >
    <filter id="grain">
      <!-- small-ish scale, low contrast -->
      <feTurbulence
        type="fractalNoise"
        baseFrequency="0.9"
        numOctaves="2"
        seed="7"
      />
      <feColorMatrix type="saturate" values="0" />
      <feComponentTransfer>
        <feFuncA type="table" tableValues="0 0.06" />
      </feComponentTransfer>
    </filter>
    <rect width="100%" height="100%" filter="url(#grain)"></rect>
  </svg>

  <!-- 2) Ledger grid (repeating gradients) -->
  <div
    class="pointer-events-none absolute inset-0 -z-10"
    style="
      background-image:
        repeating-linear-gradient(
          to right,
          rgba(0,0,0,.06) 0 1px,
          transparent 1px var(--grid)
        ),
        repeating-linear-gradient(
          to bottom,
          rgba(0,0,0,.04) 0 1px,
          transparent 1px var(--grid)
        );
    "
    aria-hidden="true"
  ></div>

  <!-- 3) Subtle uneven print / scan feel -->
  <div
    class="pointer-events-none absolute inset-0 -z-10"
    style="filter: saturate(.92) contrast(.98) brightness(1.02) blur(.2px);"
    aria-hidden="true"
  ></div>

  <!-- 4) Vignette / edge darkening -->
  <div
    class="pointer-events-none absolute inset-0 -z-10 bg-[radial-gradient(circle_at_center,transparent_70%,rgba(0,0,0,.07)_100%)]"
    aria-hidden="true"
  ></div>

  <!-- 5) Punched-hole sidebar (optional) -->
  {#if showHoles}
    <div
      class="pointer-events-none absolute inset-y-6 left-2 w-4 -z-10"
      aria-hidden="true"
    >
      {#each Array(holes) as _, i}
        <div
          class="relative my-6 h-3 w-3 rounded-none bg-white/80 shadow-[inset_0_0_0_1px_rgba(0,0,0,.12),0_2px_3px_rgba(0,0,0,.08)]"
          style="
            /* slight random offsets for imperfection */
            transform: translateX({i % 2 === 0 ? 0 : 1}px) translateY({i % 3 ===
          0
            ? 0
            : 0.5}px);
          "
        >
          <div class="absolute inset-0 rounded-none bg-black/5"></div>
        </div>
      {/each}
      <div class="absolute inset-y-0 -left-2 w-px bg-black/10"></div>
    </div>
  {/if}

  <!-- CONTENT SLOT -->
  <div class="relative px-6 py-8 md:px-10 md:py-12">
    <slot />
  </div>
</section>

<style>
  /* Fine line compensation on retina for more “printlike” edges */
  :global(.paper-label) {
    letter-spacing: 0.01em;
  }
</style>
