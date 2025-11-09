<script lang="ts">
  type Tile = {
    title: string;
    subtitle?: string;
    desc?: string;
    href: string;
    tone?: string; // background + text classes
    emblem?: string; // optional faint background mark (SVG path or emoji)
    spans?: { col?: number; row?: number }; // md+ spans
    content?: string;
  };

  export let heading = "A place for you and your family";
  export let subheading =
    "Join small groups, get involved in outreach, and discover ways for your whole family to grow in their faith.";

  // Art-directed layout to match the reference image
  export let tiles: Tile[] = [
    // Row 1 (two large)
    {
      title: "eGroup Ministry",
      subtitle: "Connecting people. Activating faith.",
      href: "/ministries/groups",
      tone: "bg-blue-700 text-white",
      spans: { col: 6, row: 2 },
      emblem:
        '<path d="M32 20c8 0 14 6 14 14s-6 14-14 14S18 42 18 34s6-14 14-14Z" fill="currentColor" opacity=".12"/>',
    },
    {
      title: "Outreach Ministry",
      subtitle: "Making an impact — locally and globally.",
      href: "/ministries/outreach",
      tone: "bg-green-600 text-white",
      spans: { col: 6, row: 2 },
      emblem:
        '<circle cx="32" cy="32" r="28" stroke="currentColor" stroke-width="8" opacity=".12" fill="none"/>',
    },

    // Row 2 (three medium)
    {
      title: "Children’s Ministry",
      subtitle: "Partnering with parents to develop kids’ faith.",
      href: "/ministries/children",
      tone: "bg-sky-600 text-white",
      spans: { col: 4, row: 2 },
      emblem:
        '<path d="M18 40c6-8 22-8 28 0" stroke="currentColor" stroke-width="8" opacity=".14" fill="none" stroke-linecap="round"/>',
    },
    {
      title: "Youth Ministry",
      subtitle: "Developing youth who influence culture.",
      href: "/ministries/youth",
      tone: "bg-zinc-900 text-white",
      spans: { col: 4, row: 2 },
      emblem:
        '<text x="12" y="44" font-size="40" font-weight="700" fill="currentColor" opacity=".12">YTH</text>',
    },
    {
      title: "Young Adult Ministry",
      subtitle: "Building community. Deepening faith.",
      href: "/ministries/young-adults",
      tone: "bg-orange-600 text-white",
      spans: { col: 4, row: 2 },
      emblem:
        '<path d="M18 20c10 12 22 12 28 0" stroke="currentColor" stroke-width="8" opacity=".12" fill="none" stroke-linecap="round"/>',
    },

    // Row 3 (full-width banner)
    {
      title: "Worship Ministry",
      subtitle:
        "Inspiring your faith and creating an atmosphere of worship to God.",
      href: "/ministries/worship",
      tone: "bg-[url('/images/worship.jpg')] bg-cover bg-center text-white",
      spans: { col: 12, row: 3 },
      emblem: "", // no emblem over photo
    },
  ];
</script>

<section aria-labelledby="bento-title" class="mx-auto max-w-7xl px-2">
  <header class="mb-6 sm:mb-8 text-center">
    <h2 id="bento-title" class="text-3xl sm:text-4xl font-bold text-white">
      {heading}
    </h2>
    <p class="mt-2 text-zinc-200 max-w-2xl mx-auto">{subheading}</p>
  </header>

  <!-- Bento grid -->
  <!-- Bento grid (hardcoded spans; no dynamic Tailwind class names) -->
  <div
    class="grid grid-cols-1 gap-3 lg:gap-4
         auto-rows-[9rem] sm:auto-rows-[9.5rem] lg:auto-rows-[10.5rem]
         md:grid-cols-12 grid-flow-dense"
  >
    {#each tiles as t, i}
      <a
        href={t.href}
        class="group relative overflow-hidden rounded-2xl ring-1 ring-black/10 p-5 sm:p-6 transition-shadow hover:shadow-xl
             md:col-span-12 md:row-span-1
             {i === 0 || i === 1 ? 'md:col-span-6 md:row-span-2' : ''}
             {i === 2 || i === 3 || i === 4
          ? 'md:col-span-4 md:row-span-2'
          : ''}
             {i === 5 ? 'md:col-span-12 md:row-span-3' : ''} 
             {t.tone ?? 'bg-white text-zinc-900'}"
      >
        {#if t.emblem}
          <svg
            class="pointer-events-none absolute inset-0 h-full w-full text-black/50 opacity-20"
            viewBox="0 0 64 64"
            fill="none"
            aria-hidden="true"
          >
            {@html t.emblem}
          </svg>
        {/if}

        <div class="relative z-10 flex h-full flex-col">
          <p class="text-xs font-medium tracking-wide opacity-80">
            {#if t.title.endsWith("Ministry")}
              {t.title}
            {:else}
              {t.subtitle}
            {/if}
          </p>

          <h3 class="mt-1 text-xl lg:text-2xl font-semibold leading-tight">
            {#if t.title.endsWith("Ministry")}
              {t.subtitle}
            {:else}
              {t.title}
            {/if}
          </h3>

          {#if t.content}
            <div class="mt-3 text-sm opacity-95">{@html t.content}</div>
          {:else if !t.title.endsWith("Ministry") && t.subtitle}
            <p class="mt-2 text-sm/6 opacity-95">{t.subtitle}</p>
          {/if}

          <span
            class="mt-auto inline-flex items-center gap-2 text-sm font-medium opacity-90 group-hover:opacity-100"
          >
            Learn more
            <svg viewBox="0 0 20 20" aria-hidden="true" class="h-4 w-4">
              <path
                fill="currentColor"
                d="M7.2 4.8a.8.8 0 011.13 0l4.8 4.8a.8.8 0 010 1.13l-4.8 4.8a.8.8 0 11-1.13-1.13L11.54 10 7.2 5.93a.8.8 0 010-1.13z"
              />
            </svg>
          </span>
        </div>
      </a>
    {/each}
  </div>
</section>
