<script lang="ts">
  import dayjs from "dayjs";
  import MobileDrawer from "./MobileDrawer.svelte";
  import Banner from "./Banner.svelte";

  // UI state
  let isMenuOpen = false;
  const toggleMenu = () => (isMenuOpen = !isMenuOpen);
  const closeMenu = () => (isMenuOpen = false);

  // Dates (single 'now')
  const now = dayjs();
  const targetDate = dayjs("2025-08-25");
  const lastDate = dayjs("2025-09-10");
  const startDate = dayjs("2025-10-08").startOf("day");
  const endDate = dayjs("2025-10-26").endOf("day");

  // Derived
  const daysUntilRevival = targetDate.diff(now, "day");
  const isBeforeEnd = now.isBefore(lastDate);
  const isLive = !now.isBefore(startDate) && !now.isAfter(endDate);

  // Flowbite
  let promoOpen = isLive;
  let isCoolModalOpen = false;

  // Reused classes / data
  const lineBase =
    "m-auto h-0.5 w-7 rounded transition-transform duration-300 bg-zinc-700 dark:bg-neutral-300";

  const navLinkClass =
    "relative block md:px-4 mx-1 px-3 py-2 rounded-lg text-zinc-700 hover:text-zinc-900 transition-colors duration-200 hover:bg-zinc-100 focus:outline-none focus-visible:ring-2 focus-visible:ring-zinc-300/70 dark:hover:bg-neutral-700/60 dark:focus-visible:ring-neutral-600/70 hover:text-sky-600";

  const desktopLinks = [
    { href: "/#discover", label: "Discover" },
    { href: "/#media", label: "Media" },
    { href: "/#events", label: "Events" },
    { href: "/#give", label: "Give" },
  ];
</script>

<!-- <Banner /> -->
<Banner id="friendsgiving-2025" href="/events/friendsgiving">
  <span class="font-semibold">Friendsgiving Lunch</span>
  <span aria-hidden="true" class="mx-1">·</span>
  <span class="whitespace-nowrap">Sat, Nov 23</span>
  <span aria-hidden="true" class="mx-1 hidden sm:inline">·</span>
  <span class="hidden sm:inline">We’ll save you a seat!</span>
</Banner>

<header
  class="sticky top-[var(--banner-h,0px)] z-40 h-20 bg-white/80 backdrop-blur-md border-b border-zinc-200"
>
  <nav class="absolute inset-x-0 top-0 h-full z-10 w-full">
    <div class="mx-auto max-w-5xl px-6 md:px-12 xl:px-6 h-full">
      <div
        class="relative flex flex-wrap items-center justify-between gap-6 py-4 md:gap-0 md:py-4"
      >
        <!-- Brand -->
        <div
          class="relative z-20 flex w-full justify-between items-center md:px-0 lg:w-max"
        >
          <a href="/#home" class="flex h-full items-center">
            <img
              src="https://ik.imagekit.io/bip1v395ybp/Logo+Wordmark(Grey)_rvMOP40oz.png?updatedAt=1761358348126"
              alt="logo"
              class="h-12 w-auto"
            />
          </a>

          <!-- Mobile hamburger -->
          <div class="relative flex max-h-10 items-center lg:hidden">
            <button
              aria-label="hamburger"
              id="hamburger"
              on:click={toggleMenu}
              class="relative p-6"
            >
              <div
                aria-hidden="true"
                id="line"
                class={lineBase}
                class:is-hidden={isMenuOpen}
                class:rotate-45={isMenuOpen}
                class:translate-y-[4px]={isMenuOpen}
                class:bg-amber-400={isMenuOpen}
              ></div>
              <div
                aria-hidden="true"
                id="line2"
                class={"m-auto mt-2 " + lineBase}
                class:rotate-[-45deg]={isMenuOpen}
                class:-translate-y-[6px]={isMenuOpen}
                class:bg-amber-400={isMenuOpen}
              ></div>
            </button>
          </div>
        </div>

        <!-- Overlay (kept) -->
        <div
          id="navLayer"
          aria-hidden="true"
          class="fixed inset-0 z-10 h-screen w-screen origin-bottom scale-y-0 bg-white/70 backdrop-blur-2xl transition duration-500 dark:bg-neutral-900/70 lg:hidden"
        ></div>

        <!-- Desktop nav -->
        <div
          id="navlinks"
          class="absolute left-0 top-full invisible z-20 flex w-full translate-y-1 scale-90 flex-col flex-wrap justify-end gap-6 rounded-3xl border border-zinc-200 bg-white p-8 opacity-0 shadow-2xl shadow-zinc-600/10 transition-all duration-300 origin-top-right
                 dark:border-neutral-700 dark:bg-neutral-800 dark:shadow-none
                 lg:visible lg:relative lg:flex lg:w-7/12 lg:translate-y-0 lg:scale-100 lg:flex-row lg:items-center lg:gap-0 lg:border-none lg:bg-transparent lg:p-0 lg:opacity-100 lg:shadow-none"
        >
          <div
            class="w-full lg:w-auto lg:pr-4 lg:pt-0 text-zinc-700 dark:text-neutral-200"
          >
            <ul
              class="flex flex-col gap-6 font-medium tracking-wide lg:flex-row lg:gap-0 primary-serif italic"
            >
              {#each desktopLinks as { href, label }}
                <li>
                  <a {href} class={navLinkClass}><span>{label}</span></a>
                </li>
              {/each}
            </ul>
          </div>
        </div>

        <MobileDrawer bind:isMenuOpen on:close={closeMenu} />
      </div>
    </div>
  </nav>
</header>
