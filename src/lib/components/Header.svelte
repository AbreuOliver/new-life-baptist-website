<script lang="ts">
  import dayjs from "dayjs";

  let isMenuOpen: boolean = false;

  function toggleMenu() {
    isMenuOpen = !isMenuOpen;
    console.log("Menu State:", isMenuOpen);
  }

  const targetDate = dayjs("2025-08-25");
  const lastDate = dayjs("2025-09-10");
  const currentDate = dayjs();

  // Calculate days until revival
  const daysUntilRevival = targetDate.diff(currentDate, "day");

  // Check if we're before the end date
  const isBeforeEnd = currentDate.isBefore(lastDate);

  const startDate = dayjs("2025-10-08").startOf("day"); // go-live date
  const endDate = dayjs("2025-10-26").endOf("day"); // inclusive through the day
  const now = dayjs();

  // Reuse the name, but make it correct and self-contained:
  const isLive = !now.isBefore(startDate) && !now.isAfter(endDate);

  // Flowbite modal open state
  let promoOpen = false;
  if (isLive) promoOpen = true; // show immediately while live

  let isCoolModalOpen = false;
</script>

<!-- <header
  class="{styling} sticky grid custom-grid-cols gap-x-clamp grid-rows-[1fr_auto] col-span-3 col-start-1 row-span-2 row-start-1 top-0 z-10 w-full h-20 md:h-18 backdrop-blur-sm"
>
  <Navbar />
</header> -->

<header
  class="sticky top-0 z-40 h-20 bg-white/80 backdrop-blur-md border-b border-zinc-200"
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

          <!-- Mobile hamburger (unchanged logic/markup) -->
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
                class="m-auto h-0.5 w-7 rounded transition-transform duration-300 bg-zinc-700 dark:bg-neutral-300"
                class:is-hidden={isMenuOpen}
                class:rotate-45={isMenuOpen}
                class:translate-y-[4px]={isMenuOpen}
                class:bg-amber-400={isMenuOpen}
              ></div>
              <div
                aria-hidden="true"
                id="line2"
                class="m-auto mt-2 h-0.5 w-7 rounded transition-transform duration-300 bg-zinc-700 dark:bg-neutral-300"
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
              <li>
                <a
                  href="/#discover"
                  class="relative block md:px-4 text-zinc-700 hover:text-zinc-900
                          after:absolute after:left-0 after:bottom-0 after:h-[2px] after:w-full after:scale-x-0 after:rounded-md after:bg-sky-600 after:transition-transform after:duration-300 after:translate-y-2 hover:after:scale-x-100"
                >
                  <span>Discover</span>
                </a>
              </li>
              <li>
                <a
                  href="/#media"
                  class="relative block md:px-4 text-zinc-700 hover:text-zinc-900
                          after:absolute after:left-0 after:bottom-0 after:h-[2px] after:w-full after:scale-x-0 after:rounded-md after:bg-sky-600 after:transition-transform after:duration-300 after:translate-y-2 hover:after:scale-x-100"
                >
                  <span>Media</span>
                </a>
              </li>
              <li>
                <a
                  href="/#events"
                  class="relative block md:px-4 text-zinc-700 hover:text-zinc-900
                          after:absolute after:left-0 after:bottom-0 after:h-[2px] after:w-full after:scale-x-0 after:rounded-md after:bg-sky-600 after:transition-transform after:duration-300 after:translate-y-2 hover:after:scale-x-100"
                >
                  <span>Events</span>
                </a>
              </li>
              <li>
                <a
                  href="/#give"
                  class="relative block md:px-4 text-zinc-700 hover:text-zinc-900
                          after:absolute after:left-0 after:bottom-0 after:h-[2px] after:w-full after:scale-x-0 after:rounded-md after:bg-sky-600 after:transition-transform after:duration-300 after:translate-y-2 hover:after:scale-x-100"
                >
                  <span>Give</span>
                </a>
              </li>
            </ul>
          </div>
        </div>

        <!-- Mobile drawer (kept, just token tweaks) -->
        <div
          class={`${isMenuOpen ? "block" : "hidden"} absolute left-0 top-20 z-20 h-[fit-content] w-screen bg-white transition-transform animate-fade-down animate-once animate-duration-500 animate-delay-100 animate-ease-linear`}
        >
          <div
            id="navlinks"
            class="absolute left-0 top-full z-20 w-[85%] translate-y-1 scale-90 origin-top-right flex-col flex-wrap justify-end gap-6 rounded-3xl border border-zinc-200 bg-white p-8 opacity-0 shadow-2xl shadow-zinc-600/10 transition-all duration-300
                   dark:border-neutral-700 dark:bg-neutral-800 dark:shadow-none
                   lg:visible lg:relative lg:hidden lg:w-7/12 lg:translate-y-0 lg:scale-100 lg:flex-row lg:items-center lg:gap-0 lg:border-none lg:bg-transparent lg:p-0 lg:opacity-100 lg:shadow-none !visible !scale-100 !opacity-100 !lg:translate-y-0"
          >
            <div
              class="w-full text-zinc-700 dark:text-neutral-200 lg:w-auto lg:pr-4 lg:pt-0"
            >
              <ul
                class="flex flex-col gap-6 tracking-wide lg:flex-row lg:gap-0 lg:text-base primary-serif italic text-xl"
              >
                <li>
                  <a
                    on:click={toggleMenu}
                    href="/#about"
                    class="block md:px-4 hover:text-sky-700 capitalize">about</a
                  >
                </li>
                <li>
                  <a
                    on:click={toggleMenu}
                    href="/#media"
                    class="block md:px-4 hover:text-sky-700 capitalize">media</a
                  >
                </li>
                <li>
                  <a
                    on:click={toggleMenu}
                    href="/#events"
                    class="block md:px-4 hover:text-sky-700 capitalize"
                    >events</a
                  >
                </li>
                <li>
                  <a
                    on:click={toggleMenu}
                    href="/#give"
                    class="block md:px-4 hover:text-sky-700 capitalize">give</a
                  >
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </nav>
</header>
