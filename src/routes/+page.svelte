<script lang="ts">
  import SmallCalendar from "$lib/components/SmallCalendar.svelte";
  import HeroOrbit from "$lib/components/HeroOrbit.svelte";
  import PaperPage from "$lib/components/PaperPage.svelte";

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
  import Footer from "$lib/components/Footer.svelte";
</script>

<div id="main" class="flex flex-col items-center space-y-0 grow min-h-40">
  <HeroOrbit
    title="A Church Centered on Jesus"
    subtitle="A loving church in White March, Maryland that believes in the life-changing power of Jesus"
    cta={{ label: "Plan Your Visit", href: "/start" }}
    secondary={{ label: "Learn More", href: "/video" }}
    items={orbitItems}
  />

  <div class="mx-auto w-screen special-serif">
    <!-- A neutral tone variant -->
    <PaperPage
      tone="cream"
      grid={300}
      showHoles={false}
      className="min-h-screen"
    >
      <h2 class="text-xl font-semibold mb-2">Proverbs 28</h2>
      <p class="text-sm text-zinc-600 leading-relaxed">
        The poor person who lives with integrity is
        <span class="underline">better</span>.
      </p>
    </PaperPage>
  </div>
</div>
<Footer />
