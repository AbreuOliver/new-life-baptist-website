<script lang="ts">
  import SmallCalendar from "$lib/components/SmallCalendar.svelte";
  import HeroOrbit from "$lib/components/HeroOrbit.svelte";

  const orbitItems = [
    { ring: 1, angle: 15, src: "/avatars/a1.jpg", alt: "A1", size: "w-8 h-8" },
    {
      ring: 1,
      angle: 120,
      src: "src/lib/icons/Prayer.icon.svelte",
      alt: "Idea",
      size: "w-7 h-7",
    },
    { ring: 2, angle: 60, src: "/avatars/a2.jpg", alt: "A2", size: "w-9 h-9" },
    {
      ring: 2,
      angle: 210,
      src: "/icons/check.svg",
      alt: "Solved",
      size: "w-7 h-7",
    },
    {
      ring: 3,
      angle: -30,
      src: "/avatars/a3.jpg",
      alt: "A3",
      size: "w-10 h-10",
    },
    {
      ring: 3,
      angle: 160,
      src: "/icons/heart.svg",
      alt: "Likes",
      size: "w-7 h-7",
    },
    {
      ring: 4,
      angle: 95,
      src: "/avatars/a4.jpg",
      alt: "A4",
      size: "w-10 h-10",
    },
    {
      ring: 4,
      angle: -140,
      src: "/icons/sparkles.svg",
      alt: "Sparkles",
      size: "w-8 h-8",
    },
  ];

  import "../global.css";
</script>

<div id="main" class="flex flex-col items-center space-y-0 grow min-h-40">
  <HeroOrbit
    title="A Church Centered on Jesus"
    subtitle="A loving church in White March, Maryland that believes in the life-changing power of Jesus"
    cta={{ label: "Plan Your Visit", href: "/start" }}
    secondary={{ label: "Learn More", href: "/video" }}
    items={orbitItems}
  />

  <!-- ********** HERO SECTION ********** -->
  <section
    class="relative w-screen overflow-hidden -mt-6 min-h-[70vhs] md:aspect-3/2"
    aria-labelledby="home-title"
  >
    <!-- Background image + color wash -->
    <figure class="absolute inset-0 isolate aspect-3/2">
      <!-- <img
        src="https://ik.imagekit.io/bip1v395ybp/new-life-auditorium_sfABCtvOw.jpg?updatedAt=1761306532683"
        alt="hero-image"
        class="absolute inset-0 h-full w-full object-cover aspect-3/2 -z-1"
      /> -->
      <video
        src="https://www.shopify.com/4c1a0f37-b3c8-4ac4-979d-e112d2201219"
        autoplay
        muted
        class="absolute inset-0 object-cover w-screen h-full"
      ></video>

      <div class="pointer-events-none absolute inset-0" aria-hidden="true">
        <div
          class="absolute inset-0 bg-gradient-to-t from-yellow-300/50 to-transparent"
        ></div>
        <div
          class="absolute inset-0 bg-gradient-to-r from-purple-500/40 to-transparent"
        ></div>
        <div
          class="absolute inset-0 bg-[radial-gradient(circle_at_15%_10%,_#cfe9ff_0%,_transparent_60%)]"
        ></div>
      </div>
    </figure>

    <div
      id="home"
      class="mx-auto w-full max-w-7xl px-6 md:px-12 xl:px-6 scroll-mt-28"
    >
      <div class="mx-auto max-w-2xl py-20 sm:py-28 text-center">
        <h1
          id="home-title"
          class="flex flex-col gap-2 sm:gap-3 text-5xl sm:text-6xl font-extrabold tracking-tight text-zinc-900 pb-8"
        >
          <span
            class="animate-fade-up animate-duration-700 animate-delay-1500 animate-ease-linear"
            >Truth.</span
          >
          <span
            class="animate-fade-up animate-duration-700 animate-delay-500 animate-ease-linear"
            >Hope.</span
          >
          <span
            class="animate-fade-up animate-duration-700 animate-delay-1000 animate-ease-linear"
            >Community.</span
          >
        </h1>

        <p class="mt-6 text-lg leading-7 text-zinc-700 z-10">
          A loving church in La Grange, NC that believes in the life-changing
          power of Jesus. Sharing His truth and hope in our community and around
          the world.
        </p>
        <div class="mt-10 flex flex-wrap items-center justify-center gap-4">
          <a
            href="/plan-your-visit"
            class="inline-flex items-center justify-center rounded-sm bg-sky-600 px-6 py-3 text-base font-semibold text-white shadow-sm hover:bg-sky-700 focus:outline-none focus-visible:ring-2 focus-visible:ring-sky-300 w-11/12 md:w-56 h-12"
          >
            Plan Your Visit
          </a>
          <a
            href="#discover"
            class="inline-flex items-center justify-center rounded-sm border border-zinc-300 bg-white px-6 py-3 text-base font-semibold text-zinc-900 hover:bg-zinc-50 focus:outline-none focus-visible:ring-2 focus-visible:ring-sky-300 w-11/12 md:w-56 h-12"
          >
            Learn More
          </a>
        </div>
      </div>

      <div
        class="mx-auto mt-6 grid w-full max-w-5xl gap-6 pb-12 sm:grid-cols-2 bg-gradient-to-b from:bg-white/50 to:bg-white"
      >
        <!-- Service Times -->
        <div class="rounded-xl border border-zinc-200 bg-white p-6 shadow-sm">
          <h2 class="mb-4 text-lg font-semibold text-zinc-900">
            Service Times
          </h2>
          <ul class="space-y-4 text-zinc-700">
            <li class="flex items-center justify-between">
              <span class="text-left">Sunday<br />Bible Study</span>
              <time class="text-right text-zinc-600">10:00 AM</time>
            </li>
            <li class="flex items-center justify-between">
              <span class="text-left">Sunday Worship</span>
              <span class="text-right text-zinc-600"
                >11:00 AM<br />&amp; 6:30 PM</span
              >
            </li>
            <li class="flex items-center justify-between">
              <span class="text-left">Wednesday<br />Prayer Meeting</span>
              <time class="text-right text-zinc-600">7:00 PM</time>
            </li>
          </ul>
        </div>

        <!-- Contact Info -->
        <div class="rounded-xl border border-zinc-200 bg-white p-6 shadow-sm">
          <h2 class="mb-4 text-lg font-semibold text-zinc-900">Contact Info</h2>
          <ul class="space-y-4 text-zinc-700">
            <li>
              <a
                href="https://www.google.com/maps/search/?api=1&amp;query=5975+US+70+East+La+Grange,+NC+28551"
                target="_blank"
                rel="noopener noreferrer"
                class="group inline-flex items-start gap-3 hover:underline"
              >
                <svg
                  class="mt-0.5 h-5 w-5 text-zinc-500"
                  viewBox="0 0 16 16"
                  fill="currentColor"
                  ><path
                    fill="currentColor"
                    fill-rule="evenodd"
                    d="m7.539 14.841l.003.003l.002.002a.755.755 0 0 0 .912 0l.002-.002l.003-.003l.012-.009a6 6 0 0 0 .19-.153a15.6 15.6 0 0 0 2.046-2.082C11.81 11.235 13 9.255 13 7A5 5 0 0 0 3 7c0 2.255 1.19 4.235 2.292 5.597a15.6 15.6 0 0 0 2.046 2.082l.189.153zM8 8.5a1.5 1.5 0 1 0 0-3a1.5 1.5 0 0 0 0 3"
                    clip-rule="evenodd"
                  ></path></svg
                >
                <span>5975 US 70 East<br />La Grange, NC 28551</span>
              </a>
            </li>
            <li>
              <a
                href="tel:+12525662170"
                class="group inline-flex items-center gap-3 hover:underline"
              >
                <svg
                  class="h-5 w-5 text-zinc-500"
                  viewBox="0 0 20 20"
                  fill="currentColor"
                  ><path
                    fill="currentColor"
                    fill-rule="evenodd"
                    d="M2 3.5A1.5 1.5 0 0 1 3.5 2h1.148a1.5 1.5 0 0 1 1.465 1.175l.716 3.223a1.5 1.5 0 0 1-1.052 1.767l-.933.267c-.41.117-.643.555-.48.95a11.54 11.54 0 0 0 6.254 6.254c.395.163.833-.07.95-.48l.267-.933a1.5 1.5 0 0 1 1.767-1.052l3.223.716A1.5 1.5 0 0 1 18 15.352V16.5a1.5 1.5 0 0 1-1.5 1.5H15c-1.149 0-2.263-.15-3.326-.43A13.02 13.02 0 0 1 2.43 8.327A13 13 0 0 1 2 5z"
                    clip-rule="evenodd"
                  ></path></svg
                >
                <span>(252) 566-2170</span>
              </a>
            </li>
            <li>
              <a
                href="mailto:info@emmanuelbaptistnc.org"
                class="group inline-flex items-center gap-3 hover:underline"
              >
                <svg
                  class="h-5 w-5 text-zinc-500"
                  viewBox="0 0 20 20"
                  fill="currentColor"
                  ><path
                    fill="currentColor"
                    fill-rule="evenodd"
                    d="M2 5a1 1 0 0 1 1-1h14a1 1 0 0 1 1 1v10a1 1 0 0 1-1 1H3a1 1 0 0 1-1-1V5zm1 0v10h14V5H3z"
                    clip-rule="evenodd"
                  ></path>
                  <path fill="currentColor" d="M4 6.5l6 4l6-4V5l-6 4l-6-4v1.5z"
                  ></path>
                </svg>
                <span>info@emmanuelbaptistnc.org</span>
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</div>
